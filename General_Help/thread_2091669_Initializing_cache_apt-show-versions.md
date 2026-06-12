---
title: "Initializing cache apt-show-versions"
date: 2012-12-05
forum: General Help
---

### Post by Alexcunn on 2012-12-05
Hello my name is Alex,

I have had several problems with my VPS. My current issue is when I try to install anything it will print an error message saying.

```
Setting up apt-show-versions (0.17) ...
** initializing cache. This may take a while **
Killed
dpkg: error processing apt-show-versions (--configure):
 subprocess installed post-installation script returned error exit status 137
E: Sub-process /usr/bin/dpkg returned an error code (1)

```I have google'd it, and there was a solution where I modified the cache ammount in apt.conf.

That did not succeed I also have tried update and upgrade. Both returned no results. I have modified my source list. It now shows this. 

```
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################
###### Ubuntu Main Repos
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted universe multi$
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted universe m$
###### Ubuntu Update Repos
deb http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted unive$
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted univer$
deb http://us.archive.ubuntu.com/ubuntu/ precise-proposed main restricted unive$
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted univ$
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted u$
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted un$
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-proposed main restricted u$
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted $
###### Ubuntu Partner Repo
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################
###### 3rd Party Binary Repos
#### GNOME3 extra apps - https://launchpad.net/~gnome3-team/+archive/gnome3
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-k$
deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu precise main
#### Google Linux Software Repositories - http://www.google.com/linuxrepositori$
## Run this command: wget -q https://dl-ssl.google.com/linux/linux_signing_key.$
deb http://dl.google.com/linux/deb/ stable non-free
#### Webmin - http://www.webmin.com
## Run this command: wget http://www.webmin.com/jcameron-key.asc -O- | sudo apt$
deb http://download.webmin.com/download/repository sarge contrib
####### 3rd Party Source Repos
#### GNOME3 extra apps (Source) - https://launchpad.net/~gnome3-team/+archive/g$
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-k$
deb-src http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu precise main
deb http://repo.ajenti.org/debian main main
deb http://download.openpanel.com/deb/ maverick main
deb-src http://download.openpanel.com/deb/ maverick main

```Anyone have any solutions?

---

### Post by Alexcunn on 2012-12-05
bump

---

### Post by Alexcunn on 2012-12-06
Is there anyone out there who has experience in this. If not I am going to do a re-install of Ubuntu.

---

### Post by oldos2er on 2012-12-06
Please be patient, and don't bump your post more than once every 24 hours. It often takes time for the "right" pair of eyes to see your post.

---

### Post by irotsoma on 2013-01-14
I'm also having an issue installing apt-show-versions as a prereq for webmin on Ubuntu 12.04.  I get:

```
Setting up apt-show-versions (0.17) ...
** initializing cache. This may take a while **
Killed
dpkg: error processing apt-show-versions (--configure):
 subprocess installed post-installation script returned error exit status 137
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Has anyone come up with a solution to this issue?

---

