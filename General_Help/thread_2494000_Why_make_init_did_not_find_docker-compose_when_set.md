---
title: "Why make init did not find docker-compose when setuping docker project ?"
date: 2024-01-02
forum: General Help
---

### Post by nilovsergey on 2024-01-02
[COLOR=#000000]
I try setup laravel app with docker container on my local kubuntu 22.04 and got error :

```
$ make init
Building containers
docker-compose build --no-cache
make: docker-compose: No such file or directory
make: *** [Makefile:13: build] Error 127


```I suppose as not long time ago docker-compose has changed it's format I got this error :


```
master@master-at-home:/Project$ sudo apt  install docker-compose
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 python3-setuptools : Depends: python3-pkg-resources (= 59.6.0-1.2) but 59.6.0-1.2ubuntu0.22.04.1 is to be installed
E: Unable to correct problems, you have held broken packages.

```

Now in my system I have :
```
master@master-at-home:/Project$ uname -a
Linux master-at-home 6.2.0-35-generic #35~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Fri Oct  6 10:23:26 UTC 2 x86_64 x86_64 x86_64 GNU/Linux
master@master-at-home:/Project$ lsb_release -d; uname -r; uname -i
Description:    Ubuntu 22.04.3 LTS
6.2.0-35-generic
x86_64

```

In docker-compose.yml of the project I found :

```
services:
    laravel.test:
        build:
            context: ./docker/8.2
            dockerfile: Dockerfile

```
No pointing to real version of docker in this docker-compose file, like I usually have in docker projects

```
    version: '3.X'
```

Why I got error with python3-setuptools package and how have I to install docker-compose ?

Would it fix my problem ?[/COLOR]

---

### Post by corey122 on 2024-01-04
It seems like the issue could be related to unmet dependencies for python3-setuptools. Try resolving the dependency conflict by running:


bash
Copy code
sudo apt-get install -f
For Docker Compose, consider installing it using pip, which might provide a more up-to-date version:


bash
Copy code
sudo apt-get remove docker-compose
sudo pip3 install docker-compose
Once resolved, use [CapCut]("https://itscapcutapk.com/") to create a tutorial video for setting up Docker projects, helping others overcome similar challenges

---

