---
title: "Installed 12.04 on a 2005 dell inspiron 2200 with celeron m and I have issue"
date: 2014-10-28
forum: General Help
---

### Post by flipside2 on 2014-10-28
Hello Everyone,

I am new to this forum, as far as actually posting comments and asking questions. Normally I simply research research research the web until I find a solution to my problems. Today I am stumped.

I am not a noob, per say, but I am not master programmer either. I have been playing around with Ubuntu for a few years now, but I usually don't have any major issues like I am having now.

My laptop has windows xp pro partitioned on one end of the 30gig hard drive, with 1gig of ram, and I tried to install the latest 14.04 ubuntu release with major performance issues. The space allocated for ubuntu is 15gigs with a 750mb allocated swap partition. Went through the whole "pae" issue just to get it to install.

I decided to down convert to 12.04 with the information I found on the web.

current known issues:

I can not install apps from the "ubuntu saftware center"....I get errors. I tried some fixes I found in these forums and other location to no avail. here is a copy/paste of what I get back when I try to "repair" the issue using the offered interface.

```
installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 170639 files and directories currently installed.) 
Unpacking linux-image-3.13.0-37-generic (from .../linux-image-3.13.0-37-generic_3.13.0-37.64~precise1_i386.deb) ... 
This kernel does not support a non-PAE CPU. 
dpkg: error processing /var/cache/apt/archives/linux-image-3.13.0-37-generic_3.13.0-37.64~precise1_i386.deb (--unpack): 
 subprocess new pre-installation script returned error exit status 1 
No apport report written because MaxReports is reached already
Examining /etc/kernel/postrm.d . 
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-37-generic /boot/vmlinuz-3.13.0-37-generic 
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-37-generic /boot/vmlinuz-3.13.0-37-generic 
Errors were encountered while processing: 
 /var/cache/apt/archives/linux-image-3.13.0-37-generic_3.13.0-37.64~precise1_i386.deb 
Error in function:  
dpkg: dependency problems prevent configuration of linux-image-generic-lts-trusty: 
 linux-image-generic-lts-trusty depends on linux-image-3.13.0-37-generic; however: 
  Package linux-image-3.13.0-37-generic is not installed. 
dpkg: error processing linux-image-generic-lts-trusty (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-generic-lts-trusty: 
 linux-generic-lts-trusty depends on linux-image-generic-lts-trusty; however: 
  Package linux-image-generic-lts-trusty is not configured yet. 
dpkg: error processing linux-generic-lts-trusty (--configure): 
 dependency problems - leaving unconfigured
```

Here is some things I have on my terminal now that I was trying to do, to no avail as well:

```
flipside@HELLSPAWN:~$ sudo apt-get autoclean
[sudo] password for flipside: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flipside@HELLSPAWN:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-generic-lts-trusty : Depends: linux-image-3.13.0-37-generic but it is not installed
E: Unmet dependencies. Try using -f.
flipside@HELLSPAWN:~$ sudo apt-get install linux-image-3.13.0-37-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  fdutils linux-lts-trusty-doc-3.13.0 linux-lts-trusty-source-3.13.0
  linux-lts-trusty-tools
The following NEW packages will be installed:
  linux-image-3.13.0-37-generic
0 upgraded, 1 newly installed, 0 to remove and 12 not upgraded.
2 not fully installed or removed.
Need to get 52.3 MB of archives.
After this operation, 148 MB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main linux-image-3.13.0-37-generic i386 3.13.0-37.64~precise1 [52.3 MB]
Fetched 52.3 MB in 1min 6s (790 kB/s)                                          
(Reading database ... 170639 files and directories currently installed.)
Unpacking linux-image-3.13.0-37-generic (from .../linux-image-3.13.0-37-generic_3.13.0-37.64~precise1_i386.deb) ...
This kernel does not support a non-PAE CPU.
dpkg: error processing /var/cache/apt/archives/linux-image-3.13.0-37-generic_3.13.0-37.64~precise1_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-37-generic /boot/vmlinuz-3.13.0-37-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-37-generic /boot/vmlinuz-3.13.0-37-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-37-generic_3.13.0-37.64~precise1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
flipside@HELLSPAWN:~$ sudo apt-get --purge remove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-generic-lts-trusty : Depends: linux-image-3.13.0-37-generic but it is not installed
E: Unmet dependencies. Try using -f.
flipside@HELLSPAWN:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-3.13.0-37-generic
Suggested packages:
  fdutils linux-lts-trusty-doc-3.13.0 linux-lts-trusty-source-3.13.0
  linux-lts-trusty-tools
The following NEW packages will be installed:
  linux-image-3.13.0-37-generic
0 upgraded, 1 newly installed, 0 to remove and 12 not upgraded.
2 not fully installed or removed.
Need to get 0 B/52.3 MB of archives.
After this operation, 148 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 170639 files and directories currently installed.)
Unpacking linux-image-3.13.0-37-generic (from .../linux-image-3.13.0-37-generic_3.13.0-37.64~precise1_i386.deb) ...
This kernel does not support a non-PAE CPU.
dpkg: error processing /var/cache/apt/archives/linux-image-3.13.0-37-generic_3.13.0-37.64~precise1_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-37-generic /boot/vmlinuz-3.13.0-37-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-37-generic /boot/vmlinuz-3.13.0-37-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-37-generic_3.13.0-37.64~precise1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
flipside@HELLSPAWN:~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-generic-lts-trusty : Depends: linux-image-3.13.0-37-generic but it is not going to be installed
 synaptic : Depends: libept1.4.12 but it is not going to be installed
            Depends: libvte9 (>= 1:0.24.0) but it is not going to be installed
            Recommends: rarian-compat but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
flipside@HELLSPAWN:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-3.13.0-37-generic
Suggested packages:
  fdutils linux-lts-trusty-doc-3.13.0 linux-lts-trusty-source-3.13.0
  linux-lts-trusty-tools
The following NEW packages will be installed:
  linux-image-3.13.0-37-generic
0 upgraded, 1 newly installed, 0 to remove and 12 not upgraded.
2 not fully installed or removed.
Need to get 0 B/52.3 MB of archives.
After this operation, 148 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 170639 files and directories currently installed.)
Unpacking linux-image-3.13.0-37-generic (from .../linux-image-3.13.0-37-generic_3.13.0-37.64~precise1_i386.deb) ...
This kernel does not support a non-PAE CPU.
dpkg: error processing /var/cache/apt/archives/linux-image-3.13.0-37-generic_3.13.0-37.64~precise1_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-37-generic /boot/vmlinuz-3.13.0-37-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-37-generic /boot/vmlinuz-3.13.0-37-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-37-generic_3.13.0-37.64~precise1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
flipside@HELLSPAWN:~$ sudo apt-get remove --purge getdeb-repository
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package getdeb-repository
flipside@HELLSPAWN:~$ sudo dpkg -i --force-overwrite /var/cache/apt/archives/linux-image-3.13.0-37-generic_3.13.0-37.64~precise1_i386.deb
(Reading database ... 170639 files and directories currently installed.)
Unpacking linux-image-3.13.0-37-generic (from .../linux-image-3.13.0-37-generic_3.13.0-37.64~precise1_i386.deb) ...
This kernel does not support a non-PAE CPU.
dpkg: error processing /var/cache/apt/archives/linux-image-3.13.0-37-generic_3.13.0-37.64~precise1_i386.deb (--install):
 subprocess new pre-installation script returned error exit status 1
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-37-generic /boot/vmlinuz-3.13.0-37-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-37-generic /boot/vmlinuz-3.13.0-37-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-37-generic_3.13.0-37.64~precise1_i386.deb
flipside@HELLSPAWN:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-generic-lts-trusty : Depends: linux-image-3.13.0-37-generic but it is not installed
E: Unmet dependencies. Try using -f.
flipside@HELLSPAWN:~$ sudo apt-get update
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                           
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg                 
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [50.7 kB]            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [98.7 kB]           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [112 kB]        
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [479 kB]       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494 B] 
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [33.0 kB]   
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,780 B] 
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [464 kB] 
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [8,000 B]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [111 kB]  
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [8,889 B]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [874 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [106 kB]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,645 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [13.2 kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [256 kB]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [15.5 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en
Fetched 2,641 kB in 17s (148 kB/s)                                             
Reading package lists... Done
flipside@HELLSPAWN:~$ 
```

I simply want my Ubuntu to work and to work effeciently, based on my availible disk space.

Any help would be greatly appriciated.

Thank you for your interest and hopeful answers.

Sincerely,
Flipside

I meant 2005 Dell Inspiron 2200. :)

---

### Post by mörgæs on 2014-10-28
Welcome to the fora.

I changed the thread title. For the PAE problem please look [here]("https://help.ubuntu.com/community/PAE").

---

### Post by flipside2 on 2014-10-28
UPDATE:

I also can not install "Ubuntu One".

The following packages have unmet dependencies,

linux-image-generic-its-trusty: depends: linux-image-3.13.0-generic but it is not installed

I have tried installing this package a few times and did everything I found on the web to fix this issue, also to no avail.

Thank You,

Flipside

---

### Post by deadflowr on 2014-10-28
Please use code tags when posting output from the terminal
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

---

### Post by flipside2 on 2014-10-28
Thank you Morgaes.

I do not have a "pae" issue. I have 12.04 installed. The "pae" issue was not allowing me to install originally. My os is just not working correctly.

```

flipside@HELLSPAWN:~$ sudo apt-get autoclean
[sudo] password for flipside: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flipside@HELLSPAWN:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-generic-lts-trusty : Depends: linux-image-3.13.0-37-generic but it is not installed
E: Unmet dependencies. Try using -f.
flipside@HELLSPAWN:~$ sudo apt-get install linux-image-3.13.0-37-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  fdutils linux-lts-trusty-doc-3.13.0 linux-lts-trusty-source-3.13.0
  linux-lts-trusty-tools
The following NEW packages will be installed:
  linux-image-3.13.0-37-generic
0 upgraded, 1 newly installed, 0 to remove and 12 not upgraded.
2 not fully installed or removed.
Need to get 52.3 MB of archives.
After this operation, 148 MB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main linux-image-3.13.0-37-generic i386 3.13.0-37.64~precise1 [52.3 MB]
Fetched 52.3 MB in 1min 6s (790 kB/s)                                          
(Reading database ... 170639 files and directories currently installed.)
Unpacking linux-image-3.13.0-37-generic (from .../linux-image-3.13.0-37-generic_3.13.0-37.64~precise1_i386.deb) ...
This kernel does not support a non-PAE CPU.
dpkg: error processing /var/cache/apt/archives/linux-image-3.13.0-37-generic_3.13.0-37.64~precise1_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-37-generic /boot/vmlinuz-3.13.0-37-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-37-generic /boot/vmlinuz-3.13.0-37-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-37-generic_3.13.0-37.64~precise1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
flipside@HELLSPAWN:~$ sudo apt-get --purge remove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-generic-lts-trusty : Depends: linux-image-3.13.0-37-generic but it is not installed
E: Unmet dependencies. Try using -f.
flipside@HELLSPAWN:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-3.13.0-37-generic
Suggested packages:
  fdutils linux-lts-trusty-doc-3.13.0 linux-lts-trusty-source-3.13.0
  linux-lts-trusty-tools
The following NEW packages will be installed:
  linux-image-3.13.0-37-generic
0 upgraded, 1 newly installed, 0 to remove and 12 not upgraded.
2 not fully installed or removed.
Need to get 0 B/52.3 MB of archives.
After this operation, 148 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 170639 files and directories currently installed.)
Unpacking linux-image-3.13.0-37-generic (from .../linux-image-3.13.0-37-generic_3.13.0-37.64~precise1_i386.deb) ...
This kernel does not support a non-PAE CPU.
dpkg: error processing /var/cache/apt/archives/linux-image-3.13.0-37-generic_3.13.0-37.64~precise1_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-37-generic /boot/vmlinuz-3.13.0-37-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-37-generic /boot/vmlinuz-3.13.0-37-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-37-generic_3.13.0-37.64~precise1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
flipside@HELLSPAWN:~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-generic-lts-trusty : Depends: linux-image-3.13.0-37-generic but it is not going to be installed
 synaptic : Depends: libept1.4.12 but it is not going to be installed
            Depends: libvte9 (>= 1:0.24.0) but it is not going to be installed
            Recommends: rarian-compat but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
flipside@HELLSPAWN:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-3.13.0-37-generic
Suggested packages:
  fdutils linux-lts-trusty-doc-3.13.0 linux-lts-trusty-source-3.13.0
  linux-lts-trusty-tools
The following NEW packages will be installed:
  linux-image-3.13.0-37-generic
0 upgraded, 1 newly installed, 0 to remove and 12 not upgraded.
2 not fully installed or removed.
Need to get 0 B/52.3 MB of archives.
After this operation, 148 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 170639 files and directories currently installed.)
Unpacking linux-image-3.13.0-37-generic (from .../linux-image-3.13.0-37-generic_3.13.0-37.64~precise1_i386.deb) ...
This kernel does not support a non-PAE CPU.
dpkg: error processing /var/cache/apt/archives/linux-image-3.13.0-37-generic_3.13.0-37.64~precise1_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-37-generic /boot/vmlinuz-3.13.0-37-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-37-generic /boot/vmlinuz-3.13.0-37-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-37-generic_3.13.0-37.64~precise1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
flipside@HELLSPAWN:~$ sudo apt-get remove --purge getdeb-repository
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package getdeb-repository
flipside@HELLSPAWN:~$ sudo dpkg -i --force-overwrite  /var/cache/apt/archives/linux-image-3.13.0-37-generic_3.13.0-37.64~precise1_i386.deb
(Reading database ... 170639 files and directories currently installed.)
Unpacking linux-image-3.13.0-37-generic (from .../linux-image-3.13.0-37-generic_3.13.0-37.64~precise1_i386.deb) ...
This kernel does not support a non-PAE CPU.
dpkg: error processing /var/cache/apt/archives/linux-image-3.13.0-37-generic_3.13.0-37.64~precise1_i386.deb (--install):
 subprocess new pre-installation script returned error exit status 1
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-37-generic /boot/vmlinuz-3.13.0-37-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-37-generic /boot/vmlinuz-3.13.0-37-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-37-generic_3.13.0-37.64~precise1_i386.deb
flipside@HELLSPAWN:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-generic-lts-trusty : Depends: linux-image-3.13.0-37-generic but it is not installed
E: Unmet dependencies. Try using -f.
flipside@HELLSPAWN:~$ sudo apt-get update
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                           
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg                 
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [50.7 kB]            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [98.7 kB]           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [112 kB]        
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [479 kB]       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494 B] 
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [33.0 kB]   
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,780 B] 
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [464 kB] 
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [8,000 B]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [111 kB]  
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [8,889 B]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [874 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [106 kB]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,645 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [13.2 kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [256 kB]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [15.5 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en
Fetched 2,641 kB in 17s (148 kB/s)                                             
Reading package lists... Done
flipside@HELLSPAWN:~$ 

```

Let us see if I did this right. I am new to forum use. Thank you Deadflowr.

---

### Post by mörgæs on 2014-10-28
If you read the text you would have noticed that it mentions Lubuntu, not Ubuntu. The latter is quite heavy for such old hardware.

---

### Post by flipside2 on 2014-10-28
Hopefully, the additional help I receive will not simply be spankings for not being thouroghly versed in the use of forum etiquette. ;)

***"If you can't laugh at the world, then you wont understand it when the world is laughing at you."*** ~Flipside-October 28th, 2014

Morgaes,

So, you belive that I should install, instead, something like Lubuntu or Xubuntu in order to get a lighter OS for my system, based on the parameters of my memory and cpu? This is why I downgraded to 12.04, because of "unity" issues on the latter distributions.

At the moment, my 12.04 Ubuntu OS is running fine, it's just got issues accessing certain apps. It is when I try to use "ubuntu software center" and install new apps, that I am having issues. Simular to the issue I am having loading "ubuntu one" onto my system. This all started when I forst loaded the os, and attempted to load "Ubuntu Tweak". 

As far as accessing apps such as "Firefox" or the web, or most all other applications currently loaded on my system, it works slower than I'd like, but fine for what I use it for.

I tried Xubuntu 14.04, and it was so slow it would freez up just accessing "Firefox" for a few seconds.

Actually, on retrospect, the issues started when there was one update that would not install. I now keep getting, "my package system is broken" errors.

```
The following packages have unmet dependencies:

linux-image-generic-lts-trusty: Depends: linux-image-3.13.0-37-generic but it is not installed

```

...and it will not install.

I hope my detailed, yet wordy explanations are helpful. ;)

Morgaes,

I have a very simular dell inspiron 2200 from 2005 that I loaded originally a 10.something distribution of ubuntu, and it worked fantastically. Not partitions or windows on that laptop. Just ubuntu with 1gig of ram and 40 gig hard drive. I can't remember the cpu proccessor off hand. I have since upgraded the OS to a 13.something distribution, and all is well. Allthough, I did have issues once I upgraded, yet I midigated those to a degree I felt comfotible with.

I have spent 48 hours straight working on this current system. Trying to install, installing, reinstalling, etc., etc. If the only fix you can suggest, based on everything I have layed out, is to download and install an even lighter OS, such as Xubuntu or Lubuntu (specifically Lubuntu), then I guess I will do that, and hope without proof that that will fix my issues. Honestly, I just refuse to belive that their is not another way in order to fix the issues I am having now without trying another OS.

Thank you for your suggestion though.

Sincerely,
Flipside

Morgaes,

Also, I changes my swappiness value to 10, and I tweeked the performance of this 12.04 Ubuntu OS using most all the helpful hints I found on these and other forums. The system runs fast enough for me. My issues seem to be package upgrading and loading issues.

Sincerely,
Flipside

I guess one question I could ask, concerning my current issues, is:

Simular to my Windows XP pro, can you use the installation media(In this case an 8gig micro SD card) to fix package issues? I use my OS installation cd to fix issues periodically on my Windows XP pro OS. Can this also be done through the installation drive for Ubuntu to reinstall missing or broken packages? Such as packages I can not seem to fix or install through the normal avenues given to me through the terminal.

By the way, I am currently on and using the 12.04 Ubuntu os as I post in this forum. Like I said, mast everything works. Just, I am unable to use "Ubuntu Software Center" to install anything, nor am I able to install anything for that matter. Based on information I have given in previous posts.

***"I guess, when you get something for free, you get what you pay for."*** ~Flipside-October 28th, 2014

I will check back later. This little black sheep needs some sleep. I have noticed my personal organic opperating system is in desperate need of a forced shutdown, Thank you all ahead of time for any and all the help you can muster. :)


[B][I]
"When we give up our personal freedoms for security, we neither deserve either, nor do we deserve anything."[/I][/B] ~Flipside-October 28th, 2014

---

### Post by grahammechanical on 2014-10-28
I think that there are some more things to clear up. What do you think Ubuntu One is? It used to be a cloud storage service provide by Ubuntu. But that has since been closed. Now Ubuntu One refers to a Single Sign On service where we can register once and the one password will log us into several Ubuntu web sites, such as this forum. Ubuntu One is not something to be installed any more..

[http://en.wikipedia.org/wiki/Ubuntu_One](http://en.wikipedia.org/wiki/Ubuntu_One)

As for the PAE issue, what does this mean?

> Unpacking linux-image-3.13.0-37-generic (from .../linux-image-3.13.0-37-generic_3.13.0-37.64~precise1_i386.deb) ...
This kernel does not support a non-PAE CPU

It tells me that the system is trying to install a kernel that is not suited to that CPU. Why do you need this kernel? The version of 12.04 that we download from Ubuntu.com would be 12.04.5. That version should already have Linux kernel 3.13 series. It should not need Linux-image-generic-lts-trusty installed to bring in kernel 3.13 series. We would install .... lts-trusty if we were running an older version of 12.04 and wanted to have the latest kernel. But then you get the issue with PAE again.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Regards.

---

### Post by flipside2 on 2014-10-29
[**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323"), Thank you!

Finally,  someone with a little more insite and gumption to look outside the box,  instead on simply offering up a 5 hour possible fix that may not even  fix my issues in the first place. Not to jab at Morgaes personally for  his understanding of my issues and non interest in actually relaying and  helping me to inderstand what those issues really are.Informing someone  to do something is one thing, but carefully explaning why you need or  want to do such an action based on valid reasoning and understanding of  that issue is something completely different.

I will, based on  your excellent expose, and carefully articulate explanation, tomorrow,  download Ubuntu 12.04.5, and install it, in order to see if this fix  fixes my issues. Don't tell Morgaes. ;)

Again, Thank You!

Sincerely,
Flipside

One day I will install a better more diverse cpu processor into both of my Inspiron 2200's, as well as a larger hard disk and ram. I so love my laptops, and want to keep enjoying them as long as technologically possible.

Partitining the hard disk into a usable windows xp/ubuntu expereince is my dream and goal. All old school like. ;)

***"Technology is the downfall of western civilization."*** ~Flipside-October 28th, 2014

---

### Post by sudodus on 2014-10-29
I think Ubuntu 12.04 LTS has good drivers for old computers, but the standard desktop interface has a heavy footprint. It is also the case with some of the standard application programs, for example the Software Center.

Fortunately there are several flavours of Ubuntu as well as ***community re-spins and distros based on 12.04 LTS, that have lighter footprints***. All of these promise support until April 2017:

- ***Precise Gnome Classic Tweaks*** by *kansasnoob*. This is possible and rather simple, since you are running Ubuntu 12.04 now. After conversion, your computer will be much more responsive. See this link (ask if you want help to install it).

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

- ***LXLE, Bento or Bodhi***. It is worth trying these ***live*** before you decide what to install.
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

---

### Post by mörgæs on 2014-10-29
I shall not annoy with more useless advice, just inform you of another example of good netiquette: 

Now the thread spans 19 posts of which 14 are yours. When you have additional information please edit your latest post in stead of adding a new one.

(Ok, I see that another moderator has compressed the thread. Thanks, Howefield)

---

### Post by flipside2 on 2014-10-29
Well, after downloading 12.04.5, and then looking at my widows download files, I noticed that the distribution I am currently using is if fact 12.04.5.

I just wanted personalized help with my issues, and I can get a bit wordy. Heck, you should see my cell phone text threads. Talk about long winded.

Not to worry though. The help I was truly looking for does not actually seem to be pressent anymore on these forums. I took a shot in the dark, based on past successes with the information I gained from this forum in the past. Apparently, now days, people expect others to follow some sort of unknown parramiters when communicating. Far be it from me to challenge the status quo in any way shape or fashion.

Be excellent to eachother! :)



Sudodus,

Thank You! [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]

After my kick in the teeth presented in my last post, I logged out and  then decided to look through past threads. Thankfully someone compressed  all my threads, so that I had no idea on the first page that someone  had provided me with useful information.

I appriciate your help. I will look into the items you have laid out and  see about implimenting them. If I need some help, I will definately  ask.

Again, I am actually on 12.04.5, not just 12.04. Sometimes the minute  details in life ellude me when excitement overtake me. Allthough, I do  try to pay attention to detail. [IMG]http://ubuntuforums.org/images/smilies/icon_wink.gif[/IMG]

Too much Jack and Cola last night. Head hurts. It's early in Texas, and damn chilly this morning.

Thank you again, and thank you to all that have attempted to help this stubborn callous primitive mulusk. [IMG]http://ubuntuforums.org/images/smilies/icon_wink.gif[/IMG]

Have a great day, afternoon, evening, night!

Flipside out.

Carpe' Diem!

---

### Post by flipside2 on 2014-10-31
UPDATE!!!

Problem solved!

Do to the awesome advice found on this forum I eventually got my head out of my nethers and finally downlaoded "Xubuntu 12.04.5", made a bootable Micro SD card, delt with the "PAE" issue again, and now everything seems to be running just fine. I do miss the interface of Ubuntu and Unity, but we can not always have what we want. We only get what we need. :)

Never forget that these people who help on these forums in most cases, if not all, do so for the love of it, and a deep desire to help others. Sometimes that can be muddled in the details.

I hope this thread helps others with simular issues in the future. If like me, you hate to trash perfectly good and usable electronics for the lastest greatest thing, that is a wasteful practice as far as I am concerned. Never been one to "Keep up with the Jones's".

Peace be with you all, and have a spectacularly wondorous life! :)

Flipside out

---

### Post by flipside2 on 2014-10-31
If I could ask a moderator to please delete all the useless and eronious information contained in this thread, and only show the pertanient information, that would be greatly appriciated. I will be deleting my account to this forum shortly. Far be it for me to be myself and not follow the rules. Tired of being spanked for being unique. Thank you.

**"When we try to control or expect others to follow our own since of morality or self righteous indignation, and not simply just accept people for the diversity and unique perspectives they bring to the table, it is our own fault if we do not enjoy the people we share this world with and the world around us."** ~Flipside-October 31st, 2014

Happy Hollows Eve!

Carpe' Diem!

---

