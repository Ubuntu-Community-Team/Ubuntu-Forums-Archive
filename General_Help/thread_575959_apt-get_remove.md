---
title: "apt-get remove"
date: 2007-10-14
forum: General Help
---

### Post by caffeine_freak on 2007-10-14
I am having trouble with apt-get remove apache2.  I tried to unistall and re-install.  apt-get says it has been removed.  When I try to reinstall it says it is already installed.     I tried the command
updatedb    I used to use this one with Red-Hat  but it did not work.   Is there a command I should use to clean up the database after uninstall so I can re-install?


sloan@sloan-server:/var$ sudo apt-get remove --purge apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  apache2*
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
Need to get 0B of archives.
After unpacking 86.0kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 84205 files and directories currently installed.)
Removing apache2 ...
sloan@sloan-server:/var$ sudo apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  apache2
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/38.7kB of archives.
After unpacking 86.0kB of additional disk space will be used.
Selecting previously deselected package apache2.
(Reading database ... 84203 files and directories currently installed.)
Unpacking apache2 (from .../apache2_2.2.3-3.2ubuntu0.1_all.deb) ...
Setting up apache2 (2.2.3-3.2ubuntu0.1) ...

sloan@sloan-server:/var$ /etc/init.d/apache2

the above command is not there and so are some others because I manually deleted them

and they are not installing on the supposed re-install

---

### Post by zvacet on 2007-10-14
```
sudo dpkg --remove --force-remove-reinstreq apache2
```

---

### Post by caffeine_freak on 2007-10-14
Ok I tried that.  But when i reinstall there are no config files in /etc/apache2

So i thought I would try a complete uninstall and then reinstall.   but when I use the below command the files in various directories are still there.      So I do not appear to be removing the whole package

Does anyone have the command for a complete removal and then reinstall?

sloan@sloan-server:~$ sudo dpkg --purge apache2
dpkg - warning: ignoring request to remove apache2 which isn't installed.
sloan@sloan-server:~$ /usr/sbin/apache
apache2         apache2ctl      apache-modconf  
sloan@sloan-server:~$ /usr/sbin/apache

---

### Post by ruibernardo on 2007-10-14
Try to remove and purge and then reinstall the "apache2.2-common" package. That's the package you want.

---

### Post by caffeine_freak on 2007-10-14
Could you share the exact commands please.  I thought I had a good handle on the proper commands but this problem has me doubting that.

Thanks

---

### Post by ruibernardo on 2007-10-14
> **caffeine_freak said:**
> Could you share the exact commands please.  I thought I had a good handle on the proper commands but this problem has me doubting that.

Thanks

 Try   this

```
sudo apt-get install apache2 apache2.2-common
```This should install both apache2 and its configuration files (in Feisty). Then, to remove them, use   

```
sudo apt-get remove apache2 apache2.2-common --purge
```

---

