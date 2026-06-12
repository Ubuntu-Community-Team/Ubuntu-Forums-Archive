---
title: "[SOLVED] Problem with package manager"
date: 2008-03-08
forum: General Help
---

### Post by azalamo99 on 2008-03-08
I have a problem that I can't seem to get fixed. I received "upgrade" notification and tried up process them. In doing so I broke my package manager. It doesn't work but still notifies me that I have several upgrades. I've been checking the forums and tried: sudo apt-get --configure -a  I keep getting this error msg:
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
dpkg: unable to open triggers ci file `/var/lib/dpkg/info/python-bittorrent.triggers': Not a directory
E: Sub-process /usr/bin/dpkg returned an error code (2)

The permissions are something I've never seen before and can't seem to find any way to deal with it.

-rw-r--r-- 1 root       root       1230618 2008-03-05 08:39 available
-rw-r--r-- 1 root       root       1230618 2008-03-05 08:38 available-old
-rw-r--r-- 1 root       root          2552 2007-12-22 11:35 diversions
pr---w-r-t 1 2153447341 4292233787       0 1969-11-10 06:22 info
-rw-r----- 1 root       root             0 2008-03-08 09:59 lock
-rw-r--r-- 1 root       root            30 2007-12-22 11:28 statoverride
-rw-r--r-- 1 root       root             0 2007-12-22 11:00 statoverride-old
-rw-r--r-- 1 root       root       1323286 2008-03-05 08:39 status
-rw-r--r-- 1 root       root       1323245 2008-03-05 08:38 status-old
drwxr-xr-x 2 root       root          4096 2008-03-08 09:53 triggers
drwxr-xr-x 2 root       root          4096 2008-03-08 09:53 updates


The problem seems to be the "info" entry.

Help.

---

### Post by bapoumba on 2008-03-08
Not sure I can help.. Never seen that either. I'll keep looking.

For now:
```
isabella@yeti:/var/lib/dpkg $ ls -la
total 6580
drwxr-xr-x  8 root root    4096 2008-03-08 09:11 .
drwxr-xr-x 62 root root    4096 2008-02-23 11:11 ..
drwxr-xr-x  2 root root    4096 2008-02-10 10:24 alternatives
-rw-r--r--  1 root root 1554722 2008-03-08 09:11 available
-rw-r--r--  1 root root 1554722 2008-03-08 09:11 available-old
-rw-r--r--  1 root root       8 2007-03-28 11:39 cmethopt
-rw-r--r--  1 root root    3444 2007-10-04 19:47 diversions
-rw-r--r--  1 root root    3383 2007-10-04 19:47 diversions-old
**drwxr-xr-x  2 root root  270336 2008-03-08 09:11 info**
-rw-r-----  1 root root       0 2008-03-08 09:12 lock
drwxr-xr-x  5 root root    4096 2007-03-28 11:44 methods
drwxr-xr-x  2 root root    4096 2007-02-20 16:43 parts
-rw-r--r--  1 root root     158 2007-10-06 19:09 statoverride
-rw-r--r--  1 root root     118 2007-10-06 19:09 statoverride-old
-rw-r--r--  1 root root 1641869 2008-03-08 09:11 status
-rw-r--r--  1 root root 1641993 2008-03-08 09:11 status-old
drwxr-xr-x  2 root root    4096 2008-02-29 09:22 triggers
drwxr-xr-x  2 root root    4096 2008-03-08 09:11 updates
```
not only the permission are strange, but the date too.

```

isabella@yeti:/var/lib/dpkg/info $ ls -la python-bi*
-rw-r--r-- 1 root root 2752 2007-11-14 16:33 python-bittorrent.list
-rw-r--r-- 1 root root 3588 2007-10-29 19:11 python-bittorrent.md5sums
-rwxr-xr-x 1 root root  173 2007-10-29 19:11 python-bittorrent.postinst
-rwxr-xr-x 1 root root  834 2007-10-29 19:11 python-bittorrent.prerm
```

```
isabella@yeti:/var/cache/debconf $ ls -la
total 5940
drwxr-xr-x  2 root root    4096 2008-03-08 09:10 .
drwxr-xr-x 18 root root    4096 2007-07-21 22:56 ..
-rw-r--r--  1 root root   48023 2008-02-10 10:24 config.dat
-rw-r--r--  1 root root   48022 2008-02-10 10:22 config.dat-old
-rw-------  1 root root     654 2007-07-20 11:02 passwords.dat
-rw-r--r--  1 root root 2978978 2008-03-08 09:10 templates.dat
-rw-r--r--  1 root root 2978978 2008-03-08 09:10 templates.dat-old
```

(and I suppose you ran sudo dpkg --configure -a, and not apt-get, because I do not know of a --configure option with apt-get ;))

Please post your sources.list (cat /etc/apt/sources.list) and the errors to:
```
sudo apt-get update
sudo apt-get dist-upgrade

```

---

### Post by azalamo99 on 2008-03-08
azalamo99@azalamo99:~$ cat /etc/apt/sources.list
## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates restricted main multiverse universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy-commercial main

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main multiverse universe
azalamo99@azalamo99:~$ 

-----------------------------------------------------------------------------------------------------------------

azalamo99@azalamo99:~$ sudo apt-get update
[sudo] password for azalamo99:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US           
Get:3 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release.gpg [191B]       
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Translation-en_US            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US  
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg [191B] 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages    
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages
Fetched 5B in 3s (2B/s)  
Reading package lists... Done
azalamo99@azalamo99:~$ 

------------------------------------------------------------------------------------------------------------------

azalamo99@azalamo99:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  evolution evolution-common evolution-plugins tzdata wine wine-dev
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/26.9MB of archives.
After unpacking 303kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
dpkg: unable to open triggers ci file `/var/lib/dpkg/info/python-bittorrent.triggers': Not a directory
E: Sub-process /usr/bin/dpkg returned an error code (2)
azalamo99@azalamo99:~$ 


Your right I did mean : "sudo dpkg --configure -a"  sorry. I'm been typing cmds and not keeping track of what works and what doesn't. Thanks for looking at this for me. I have a feeling I am going to have to re-install Ubuntu 7.10 :(

---

### Post by azalamo99 on 2008-03-09
I think I have straightened most of this mess out. I removed the offending "whatever that was" that the "info" directory had in it and made a new directory called info in it's place. Then after a few more tweaks (chmod, chown, etc) got most of the updates to finally work. There is one : tzdata that still is giving me a problem with some mysterious message:
E: tzdata: subprocess post-installation script returned error exit status 1
But my time zone is showing correctly and the "new update notification" is no longer showing.

I wish these "automatic updates" didn't screw up my already working system! It is getting to be a real pain to keep my system updated when this happens. Cmon fellows this lilnux stuff is hard enough to learn without you throwing me these monkey wrenches!

---

### Post by itsjustarumour on 2008-03-09
> **azalamo99 said:**
> I think I have straightened most of this mess out. I removed the offending "whatever that was" that the "info" directory had in it and made a new directory called info in it's place. Then after a few more tweaks (chmod, chown, etc) got most of the updates to finally work. There is one : tzdata that still is giving me a problem with some mysterious message:
E: tzdata: subprocess post-installation script returned error exit status 1
But my time zone is showing correctly and the "new update notification" is no longer showing.

I wish these "automatic updates" didn't screw up my already working system! It is getting to be a real pain to keep my system updated when this happens. Cmon fellows this lilnux stuff is hard enough to learn without you throwing me these monkey wrenches!

I got exactly the same problem with tzdata since the automatic updates a few days ago - ie "E: tzdata: subprocess post-installation script returned error exit status 1" .  I've posted on this elsewhere on the forums but nobody has been able to advise on a fix, although I've come across at least 2 other peeps getting exactly the same problem.  In both cases they were advised to just reinstall Ubuntu, which isn't really acceptable for me considering the amount of time and energy I've invested over four months getting most things working.  So I'd just like to echo azalamo99's comments - come on Ubuntu/Canonical, stop breaking our systems with automatic updates!!


EDIT - I've managed to fix my problem with tzdata and the "E: tzdata: subprocess post-installation script returned error exit status 1" error message due to "debconf: DbDriver "config": could not open /var/cache/debconf/config.dat".  See my post here for details:

[http://ubuntuforums.org/showthread.php?p=4483796#post4483796](http://ubuntuforums.org/showthread.php?p=4483796#post4483796)  :-)

Azalamo99 - you might want to check this out, it might fix your final problem!

---

