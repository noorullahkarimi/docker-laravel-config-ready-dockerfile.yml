
# docker-laravel-config-ready-dockerfile.yml

## Project description

we prepared a project docker with config to speed up for you. you don't need to write this configs at the first. if you want to learn or compare with your project or you want a ready config, it can help you.( LOL ).

##  Directory structure

-   `nginx`: The config of the nginx is here .
-   `src`: Your code project will be here and you should put your code in.
-   `dockerfile`: This is the config of docker.
-   `docker-compose.yml`  It is include of the config mysql and php and etc.

## How to run :

###  Prerequisites

-   Docker Desktop ( I use Docker version 20.10.21) but I don't think it make problem in different version.
-   WSL2 (ubuntu)
-  windows 10 (I don't test it on the linux but I think it work with some changes) also if for install docker you should install the WSL2 so your windows will be OK with this project.
-  and good internet connection ,LOL.(because docker download dependency by itself)

### how to config docker for laravel project

 1. go to dockerfile:
 at the first you need change the php version on line 1.

	
	> FROM  php:7.4-fpm-alpine

	it is for the version php .(alpine version mean it is lighter version and not actully full complete version. but it is work for me . if you don't want, you can change it simple.

 2. go to <code>docker-compose.yml</code>
in this file you can see all config you need it like php, mysql, phpmyadmin, nginx, npm, artisan.
 - you can change the **volums** as you want.( **volume** are the place that docker save changes in projct on your ubunto).
 - you can change the **images** as you want( **images** are the version of the dependency you need to them. ( **for Example** mysql version 5.7).
 - you can change **container_name** as you want. **be aware** , every project you make a container for, you should change the **container_name**. if you don't maybe you get the error for the same name.
 - also you can change you ports in every service. the secound port is the port on your container and first port is the port on your computer.
 
### what is now?
___
open the shell ( linux subsystem ) and put the command below:

> docker-compose run -d --build

it auto download the images you putted on the <code>docker-compose.yml </code> .
after download, if you want to use artisn , the command be like:

>  docker-compose run --rm artisan migrate

### issue with docker
Docker always have more usage of cpu and memory with no limited.
if you want to reduce usage and make limite for that, the simplest way is limit the **WSL2** in your computer. 
At the first go to this path in your computer 

> C:\Users\<your computer name or root user>

Make a file with name <code>.wslconfig</code>
**NOTICE: exactly this name with dot at the first of name.**
now put the config below in:

> [wsl2]
> 
>  memory=2GB
> 
> processors=2

Choose your memory limit and cpu core for your **WSL2** it make limited and docker can not use more. of course we have different way but this one is one of them.
**NOTICE** : if you reduce too much of cpu and memory maybe have some error. I wrote 1 core and 1 memory and get the **504-gatway time out**.
if your computer when you work with docker make overheat, please disable the auto updater from **Docker Desktop** setting. also disable it from startup programs in task manager.


### final discuse
if you see this project usefull, please put start on repository adn follow us .
if you see problem, please put issue.
thanks for support :))
