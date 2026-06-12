---
title: "How to install vue/cli app under docker"
date: 2020-01-01
forum: General Help
---

### Post by petrogromovo on 2020-01-01
Hello!
I want to install my @vue/cli 4.0.5 app under docker and I found package ebiven/vue-cli 

looking at demo at [https://github.com/ebiven/docker-vue-cli](https://github.com/ebiven/docker-vue-cli) I see that 
ebiven/docker-vue-cli is used as web container, so removing node_modules directory and I remade my _Docker/docker-compose.yml :

```
version: '3.5'

services:



    web:
        container_name: vtasks_web

        image: ebiven/vue-cli

        command: npm install
#        command: npm install ; npm run serve  // I GOT ERROR HERE
#        command: npm run serve

        build:
            context: ./web
            dockerfile: Dockerfile.yml

        environment:
            - APACHE_RUN_USER=www-data

        volumes:
            - ${APP_PATH_HOST}:${APP_PTH_CONTAINER}
        ports:
            - "8088:80"

        working_dir: ${APP_PTH_CONTAINER}


    db:
        container_name: vtasks_db
        image: mysql:5.7.28
        restart: always
        environment:
            - MYSQL_DATABASE=DockerVTasks
            - MYSQL_USER=docker_user
            - MYSQL_PASSWORD=4321
            - MYSQL_ALLOW_EMPTY_PASSWORD=false
            - MYSQL_ROOT_PASSWORD=321
            - TZ=Europe/Kiev

        volumes:
            - ${DB_PATH_HOST}:/var/lib/mysql


    adminer:
      container_name: vtasks_adminer
      image: adminer
      restart: always
      ports:
        - 8089:8080
      links:
        - db

```
as result I see :

```
$ docker-compose up -d --build     
Building web
Step 1/6 : FROM php:7.3-apache
 ---> 5af347316d4b
Step 2/6 : RUN apt-get update &&     apt-get install -y     python     libfreetype6-dev     libwebp-dev     libjpeg62-turbo-dev     libpng-dev     libzip-dev     nano     mc     git-core     curl     build-essential     openssl     libssl-dev     libgmp-dev     libldap2-dev     netcat     locate     && git clone https://github.com/nodejs/node.git     && cd node     && git checkout v12.0.0     && ./configure      && make      && make install
 ---> Using cache
 ---> b56b2543f6bd
Step 3/6 : RUN npm install cross-env
 ---> Using cache
 ---> f8abda742c47
Step 4/6 : RUN  docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-webp-dir=/usr/include/  --with-jpeg-dir=/usr/include/
 ---> Using cache
 ---> df0636ba5b86
Step 5/6 : RUN  docker-php-ext-install gd pdo pdo_mysql zip gmp bcmath pcntl ldap sysvmsg exif && a2enmod rewrite
 ---> Using cache
 ---> 307c9f243f02
Step 6/6 : COPY virtualhost.conf /etc/apache2/sites-enabled/000-default.conf
 ---> Using cache
 ---> 3c733883faaa

Successfully built 3c733883faaa
Successfully tagged ebiven/vue-cli:latest
Recreating vtasks_web ... 
vtasks_db is up-to-date
Recreating vtasks_web
Recreating vtasks_web ... done
serge@athoe:/mnt/_work_sdb8/wwwroot/lar/VApps/vtasks/_Docker$ docker logs --tail=40  vtasks_web

> node-sass@4.13.0 install /var/www/vtasks_docker_root/node_modules/node-sass
> node scripts/install.js

Downloading binary from https://github.com/sass/node-sass/releases/download/v4.13.0/linux-x64-72_binding.node
Download complete
Binary saved to /var/www/vtasks_docker_root/node_modules/node-sass/vendor/linux-x64-72/binding.node
Caching binary to /root/.npm/node-sass/4.13.0/linux-x64-72_binding.node

> core-js@3.6.1 postinstall /var/www/vtasks_docker_root/node_modules/core-js
> node -e "try{require('./postinstall')}catch(e){}"

Thank you for using core-js ( https://github.com/zloirock/core-js ) for polyfilling JavaScript standard library!

The project needs your help! Please consider supporting of core-js on Open Collective or Patreon: 
> https://opencollective.com/core-js 
> https://www.patreon.com/zloirock 

Also, the author of core-js ( https://github.com/zloirock ) is looking for a good job -)


> ejs@2.7.4 postinstall /var/www/vtasks_docker_root/node_modules/ejs
> node ./postinstall.js

Thank you for installing EJS: built with the Jake JavaScript build tool (https://jakejs.com/)


> node-sass@4.13.0 postinstall /var/www/vtasks_docker_root/node_modules/node-sass
> node scripts/build.js

Binary found at /var/www/vtasks_docker_root/node_modules/node-sass/vendor/linux-x64-72/binding.node
Testing binary
Binary is fine
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.11 (node_modules/fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.11: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})

added 1239 packages from 876 contributors and audited 19413 packages in 26.747s
found 0 vulnerabilities


```I see node_modules directory is generated, but also I need to run
```
npm run serve

```after 

```
*[COLOR=#808080]npm install[/COLOR]*

```

But which syntax have I to use?

---

### Post by petrogromovo on 2020-01-09
Who has installed vue/cli app under docker please share your expierence...

---

