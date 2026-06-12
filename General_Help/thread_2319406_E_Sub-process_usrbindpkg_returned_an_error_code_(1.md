---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2016-04-03
forum: General Help
---

### Post by Dillon_Funderburg on 2016-04-03
Hi! So I have seen multiple of these error codes on this website. But everything I try doesnt work. So I figured I'd make my own post and get help. I get this code every time I attempt to install anything. But for sake of understanding. We're going to talk about attempting to install PlayOnLinux. So ill just post my whole terminal code and then go from there..

 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of git-daemon-run:
 git-daemon-run depends on runit; however:
  Package runit is not configured yet.


dpkg: error processing package git-daemon-run (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 runit
 git-daemon-run
addictedgmr@AddictedGmr:~$ sudo apt-get remove --purge getdeb-repository
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package getdeb-repository
addictedgmr@AddictedGmr:~$ sudo dpkg -i --force-overwrite /var/cache/apt/archives/libogremain-1.7.3_1.7.3-ogredev-natty3_i386.deb
dpkg: error processing archive /var/cache/apt/archives/libogremain-1.7.3_1.7.3-ogredev-natty3_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/libogremain-1.7.3_1.7.3-ogredev-natty3_i386.deb
addictedgmr@AddictedGmr:~$ clear


addictedgmr@AddictedGmr:~$ sudo wget -q "http://deb.playonlinux.com/public.gpg" -O- | sudo apt-key add -
OK
addictedgmr@AddictedGmr:~$ sudo wget [http://deb.playonlinux.com/playonlinux_precise.list](http://deb.playonlinux.com/playonlinux_precise.list) -O /etc/apt/sources.list.d/playonlinux.list
--2016-04-03 20:41:20--  [http://deb.playonlinux.com/playonlinux_precise.list](http://deb.playonlinux.com/playonlinux_precise.list)
Resolving deb.playonlinux.com (deb.playonlinux.com)... 51.254.83.230, 2001:41d0:2:37ca::1e
Connecting to deb.playonlinux.com (deb.playonlinux.com)|51.254.83.230|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 45
Saving to: ‘/etc/apt/sources.list.d/playonlinux.list’


/etc/apt/sources.li 100%[=====================>]      45  --.-KB/s   in 0s     


2016-04-03 20:41:20 (2.38 MB/s) - ‘/etc/apt/sources.list.d/playonlinux.list’ saved [45/45]


addictedgmr@AddictedGmr:~$ sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily InRelease
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily InRelease                           
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) precise InRelease                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main amd64 Packages                          
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) precise/main amd64 Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/universe amd64 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/restricted amd64 Packages    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main i386 Packages               
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) precise/main i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/multiverse amd64 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/main i386 Packages           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/universe i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/restricted i386 Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/multiverse i386 Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/universe Translation-en
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) precise/main Translation-en_US
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) precise/main Translation-en
Reading package lists... Done                                                  
addictedgmr@AddictedGmr:~$ sudo apt-get install playonlinux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
playonlinux is already the newest version.
The following packages were automatically installed and are no longer required:
  fonts-horai-umefont fonts-unfonts-core fonts-wqy-microhei
  gnome-exe-thumbnailer libavahi-common-data:i386 libcapi20-3 libodbc1
  libosmesa6 odbcinst odbcinst1debian2 ttf-wqy-microhei unixodbc
  wine-gecko2.21 wine-gecko2.21:i386 wine-mono0.0.8
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up runit (2.1.2-3ubuntu1) ...
start: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
dpkg: error processing package runit (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of git-daemon-run:
 git-daemon-run depends on runit; however:
  Package runit is not configured yet.


dpkg: error processing package git-daemon-run (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 runit
 git-daemon-run
E: Sub-process /usr/bin/dpkg returned an error code (1)
addictedgmr@AddictedGmr:~$ sudo apt-get install curl p7zip-full p7zip-rar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
p7zip-full is already the newest version.
p7zip-full set to manually installed.
curl is already the newest version.
The following packages were automatically installed and are no longer required:
  fonts-horai-umefont fonts-unfonts-core fonts-wqy-microhei
  gnome-exe-thumbnailer libavahi-common-data:i386 libcapi20-3 libodbc1
  libosmesa6 odbcinst odbcinst1debian2 ttf-wqy-microhei unixodbc
  wine-gecko2.21 wine-gecko2.21:i386 wine-mono0.0.8
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  p7zip-rar
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 44.5 kB of archives.
After this operation, 147 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily/multiverse p7zip-rar amd64 9.20.1~ds.1-3 [44.5 kB]
Fetched 44.5 kB in 0s (76.8 kB/s)    
Selecting previously unselected package p7zip-rar.
(Reading database ... 219404 files and directories currently installed.)
Preparing to unpack .../p7zip-rar_9.20.1~ds.1-3_amd64.deb ...
Unpacking p7zip-rar (9.20.1~ds.1-3) ...
Setting up runit (2.1.2-3ubuntu1) ...
start: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
dpkg: error processing package runit (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of git-daemon-run:
 git-daemon-run depends on runit; however:
  Package runit is not configured yet.


dpkg: error processing package git-daemon-run (--configure):
 dependency problems - leaving unconfigured
Setting up p7zip-rar (9.20.1~ds.1-3) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 runit
 git-daemon-run
E: Sub-process /usr/bin/dpkg returned an error code (1)
addictedgmr@AddictedGmr:~$ 


I get these codes every single thing I attempt to install.. I really need help. Im new to Linux, So I don't know too much about any of this. Haha.

Thanks, Dillon

---

