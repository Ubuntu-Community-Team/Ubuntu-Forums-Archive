---
title: "Sources.list empty"
date: 2013-03-22
forum: General Help
---

### Post by UltraV on 2013-03-22
Sorry, I am very new to working with Linux and in a Command Prompt Only environment. When trying to get my network working on Ubuntu Server 12.04.2 I somehow deleted the sources.list and now it is empty. How can I get it back? I installed via CD-ROM.

Trying to install Webmin and I am having issues trying to get it installed, webmin guide said to make sure something isn't commented out in the sources.list and when I checked it was empty...

Thanks

---

### Post by papibe on 2013-03-22
Hi UltraV. Welcome to tht forums ):P

Sorry to hear that. There' a online website that can generate the file based on your Ubuntu version. See [here]("http://askubuntu.com/questions/124017/how-do-i-restore-the-default-repositories") for details.

Let us know how it goes.
Regards.

---

### Post by UltraV on 2013-03-22
Hi, Thanks. I followed that and updated the sources.list but still can't install webmin. Keeps giving me:

E: Package 'libnet-ssleay-perl' has no installation candidate   ----same goes for:
libauthen-pam-perl
libio-pty-perl
apt-show-versions

---

### Post by papibe on 2013-03-22
Could you post your new sources.list?

Regards.

EDIT: don't forget to update your sources before trying to install anything:
```
sudo apt-get update
```

---

### Post by UltraV on 2013-03-22
Here is what I put in:
```
###### Ubuntu Main Repos
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse 

###### Ubuntu Extras Repo
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### Webmin - http://www.webmin.com
## Run this command: wget http://www.webmin.com/jcameron-key.asc -O- | sudo apt-key add -
deb http://download.webmin.com/download/repository sarge contrib
```

and I did the sudo update

---

### Post by UltraV on 2013-03-22
I think I just figured it out, I missed an (s) in the extras part of the deb-src :(

---

