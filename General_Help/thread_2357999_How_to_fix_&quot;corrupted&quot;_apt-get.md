---
title: "How to fix &quot;corrupted?&quot; apt-get"
date: 2017-04-08
forum: General Help
---

### Post by pizzipie on 2017-04-08
Is there a way to fix or re-install apt-get on my Ubuntu 14.04 OS. Can a new** /etc/apt/sources.list** be created?

**apt-get update:** hangs up waiting forever for headers with lots of ign and err and hit. no gets.

**apt-get upgrade:** hangs up waiting forever for headers. **Says packages are "Not Authenticated"**.

Packages show up in Synaptic as not installed when they actually work (libreOffice Base for instance). 

It seems that I got into this mess when I last used the 'update software' app that appears  periodically at the bottom of the screen. Included Firefox 52.xx I got messages that it couldn't access a bunch of stuff. It hasn't worked since.

Thanks for help with fixing this.

R

```
rick@rick-Latitude-E6510:~$ sudo apt-get update
[sudo] password for rick: 
Ign http://dl.google.com testing InRelease                                     
Ign http://dl.google.com testing Release.gpg                                   
Hit http://ppa.launchpad.net trusty InRelease                                  
Ign http://dl.google.com testing Release                                       
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://archive.canonical.com trusty InRelease                              
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://archive.canonical.com trusty Release                                
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.canonical.com trusty/partner Translation-en                 
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Err http://dl.google.com testing/non-free amd64 Packages                       
  404  Not Found [IP: 2607:f8b0:400a:808::200e 80]
Err http://dl.google.com testing/non-free i386 Packages                        
  404  Not Found [IP: 2607:f8b0:400a:808::200e 80]
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign http://dl.google.com testing/non-free Translation-en_US                    
Ign http://dl.google.com testing/non-free Translation-en                       
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://dl.google.com testing/non-free Translation-en_CA                    
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Ign http://extras.ubuntu.com trusty/main Translation-en               
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign http://extras.ubuntu.com trusty/main Translation-en_CA                     
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty/main amd64 Packages                
Hit http://ppa.launchpad.net trusty/main i386 Packages             
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-en_CA                     
Ign http://archive.ubuntu.com trusty InRelease                                 
Ign http://security.ubuntu.com trusty-security InRelease
100% [Waiting for headers] [Waiting for headers]
```

---

### Post by oldos2er on 2017-04-08
Which repository server are you using? Sometimes switching to the main server can fix this.

Can we see your sources? ```
cat /etc/apt/sources.list

ll /etc/apt/sources.list.d/
``` Please copy/paste all the output text into a post here rather than attaching a file.

Also if you could tell us what type of internet connection you use, wired or wireless.

---

### Post by pizzipie on 2017-04-08
> Which repository server are you using? Sometimes switching to the main server can fix this.

I don't know.

> what type of internet connection you use, wired or wireless.                 

I am using wireless.

**Here is: /etc/sources.list**

rick@rick-Latitude-E6510:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)]/ trusty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main

**Here is: ll /etc/apt/sources.list.d/**

rick@rick-Latitude-E6510:~$ ll /etc/apt/sources.list.d/
total 80
drwxr-xr-x 2 root root 4096 Feb 11 13:54 ./
drwxr-xr-x 6 root root 4096 Feb 11 13:55 ../
-rw-r--r-- 1 root root  160 Feb 13 10:07 andreas-diesner-garminplugin-trusty.list
-rw-r--r-- 1 root root  160 Feb 13 10:07 andreas-diesner-garminplugin-trusty.list.save
-rw-r--r-- 1 root root   53 Feb 13 10:07 google.list
-rw-r--r-- 1 root root   53 Feb 13 10:07 google.list.save
-rw-r--r-- 1 root root  198 Feb 13 10:07 noobslab-apps-trusty.list
-rw-r--r-- 1 root root  198 Feb 13 10:07 noobslab-apps-trusty.list.save
-rw-r--r-- 1 root root   62 Feb 13 10:07 Org.mariadb.list
-rw-r--r-- 1 root root   62 Feb 13 10:07 Org.mariadb.list.save
-rw-r--r-- 1 root root  174 Feb 13 10:07 qbittorrent-team-qbittorrent-stable-trusty.list
-rw-r--r-- 1 root root  174 Feb 13 10:07 qbittorrent-team-qbittorrent-stable-trusty.list.save
-rw-r--r-- 1 root root  132 Feb 13 10:07 samrog131-ppa-trusty.list
-rw-r--r-- 1 root root  132 Feb 13 10:07 samrog131-ppa-trusty.list.save
-rw-r--r-- 1 root root  134 Feb 13 10:07 ubuntu-wine-ppa-trusty.list
-rw-r--r-- 1 root root  134 Feb 13 10:07 ubuntu-wine-ppa-trusty.list.save
-rw-r--r-- 1 root root  144 Feb 13 10:07 vovansrnd-coolreader-trusty.list
-rw-r--r-- 1 root root  144 Feb 13 10:07 vovansrnd-coolreader-trusty.list.save
-rw-r--r-- 1 root root  134 Feb 13 10:07 xorg-edgers-ppa-trusty.list
-rw-r--r-- 1 root root  134 Feb 13 10:07 xorg-edgers-ppa-trusty.list.save
rick@rick-Latitude-E6510:~$

[B]Here is: apt-get install example

[/B]rick@rick-Latitude-E6510:~$ sudo apt-get install finger
[sudo] password for rick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  finger
0 upgraded, 1 newly installed, 0 to remove and 31 not upgraded.
Need to get 17.3 kB of archives.
After this operation, 68.6 kB of additional disk space will be used.
WARNING: The following packages **cannot be authenticated!            <<= NOTE:**
  finger
Install these packages without verification? [y/N] y
0% [Waiting for headers]

---

