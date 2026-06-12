---
title: "Ubuntu LibreOffice fails to install as in conflict with OpenOffice"
date: 2016-04-17
forum: General Help
---

### Post by Nahua_Kang on 2016-04-17
**### Update1: I have done several steps following ian-weisser's instructions on the post [http://ubuntuforums.org/showthread.php?t=2248157](http://ubuntuforums.org/showthread.php?t=2248157) but I am not sure yet if I fixed the issue of this conflict between LibreOffice and OpenOffice. Moreover, I don't know why OpenOffice keeps crashing and LibreOffice's Impress did not work. Is it because I still have Windows on my laptop? Please if anyone could help it would be highly appreciated!**
[B]
### Update2: Since no one is helping, I assumed my question is too simple to bother others. After following most steps mentioned by ian-weisser on the post listed above, I attempted to install LibreOffice again and it seems to be working this time.[/B]

Hi! I removed LibreOffice and installed OpenOffice but found out that OpenOffice fails to work on my laptop (goes to black screen and then log out each time I use it).
Right now I'm trying to remove OpenOffice and reinstall LibreOffice but run into the problem below.
Have tried several codes to resolve it but still cannot fix it. Please let me know if any of you can help! Thank you very much!

```

installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 205201 files and directories currently installed.)
Preparing to unpack .../libreoffice-common_1%3a5.1.2~rc2-0ubuntu1~trusty0_all.deb ...
Unpacking libreoffice-common (1:5.1.2~rc2-0ubuntu1~trusty0) ...
dpkg: error processing archive /var/cache/apt/archives/libreoffice-common_1%3a5.1.2~rc2-0ubuntu1~trusty0_all.deb (--unpack):
 trying to overwrite '/usr/bin/soffice', which is also in package openoffice-debian-menus 4.1.2-9782
rmdir: failed to remove /var/lib/libreoffice/share/prereg/: No such file or directory
rmdir: failed to remove /var/lib/libreoffice/share/: No such file or directory
rmdir: failed to remove /var/lib/libreoffice/program/: No such file or directory
rmdir: failed to remove /var/lib/libreoffice: No such file or directory
rmdir: failed to remove /var/lib/libreoffice: No such file or directory
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Processing triggers for gnome-icon-theme (3.10.0-0ubuntu2) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a5.1.2~rc2-0ubuntu1~trusty0_all.deb
Error in function: 
dpkg: dependency problems prevent configuration of libreoffice-style-human:
 libreoffice-style-human depends on libreoffice-common; however:
  Package libreoffice-common is not installed.


dpkg: error processing package libreoffice-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-java-common:
 libreoffice-java-common depends on libreoffice-common; however:
  Package libreoffice-common is not installed.


dpkg: error processing package libreoffice-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-style-elementary:
 libreoffice-style-elementary depends on libreoffice-common; however:
  Package libreoffice-common is not installed.


dpkg: error processing package libreoffice-style-elementary (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-sdbc-hsqldb:
 libreoffice-sdbc-hsqldb depends on libreoffice-java-common (>= 1:5.1.2~rc2~); however:
  Package libreoffice-java-common is not configured yet.


dpkg: error processing package libreoffice-sdbc-hsqldb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-style-galaxy:
 libreoffice-style-galaxy depends on libreoffice-common; however:
  Package libreoffice-common is not installed.


dpkg: error processing package libreoffice-style-galaxy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-ogltrans:
 libreoffice-ogltrans depends on libreoffice-common; however:
  Package libreoffice-common is not installed.

```

---

### Post by Nahua_Kang on 2016-04-17
Trying to follow ian-weisser on the post: [http://ubuntuforums.org/showthread.php?t=2183609](http://ubuntuforums.org/showthread.php?t=2183609)
When I run:
```

sudo apt-get remove openoffice-debian-menus

```
I get the following results:
```

sudo apt-get remove openoffice-debian-menus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:5.1.2~rc2) but it is not going to be installed
 libreoffice-java-common : Depends: libreoffice-common but it is not going to be installed
 libreoffice-ogltrans : Depends: libreoffice-common but it is not going to be installed
 libreoffice-style-elementary : Depends: libreoffice-common but it is not going to be installed
 libreoffice-style-galaxy : Depends: libreoffice-common but it is not going to be installed
 libreoffice-style-human : Depends: libreoffice-common but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by Nahua_Kang on 2016-04-17
Running again:
```

sudo apt-get autoremove openoffice-debian-menus libreoffice-core libreoffice-java-common libreoffice-ogltrans libreoffice-style-elementary libreoffice-style-galaxy libreoffice-style-human

```

Get results:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice : Depends: libreoffice-core (= 1:5.1.2~rc2-0ubuntu1~trusty0) but it is not going to be installed
               Depends: libreoffice-java-common (>= 1:5.1.2~rc2~) but it is not going to be installed
 libreoffice-avmedia-backend-gstreamer : Depends: libreoffice-core but it is not going to be installed
 libreoffice-base : Depends: libreoffice-core (= 1:5.1.2~rc2-0ubuntu1~trusty0) but it is not going to be installed
                    Recommends: libreoffice-java-common (>= 1:5.1.2~rc2~) but it is not going to be installed
 libreoffice-base-core : Depends: libreoffice-core (= 1:5.1.2~rc2-0ubuntu1~trusty0) but it is not going to be installed
 libreoffice-base-drivers : Depends: libreoffice-core but it is not going to be installed
 libreoffice-calc : Depends: libreoffice-core (= 1:5.1.2~rc2-0ubuntu1~trusty0) but it is not going to be installed
 libreoffice-draw : Depends: libreoffice-core (= 1:5.1.2~rc2-0ubuntu1~trusty0) but it is not going to be installed
 libreoffice-gnome : Depends: libreoffice-core (= 1:5.1.2~rc2-0ubuntu1~trusty0) but it is not going to be installed
 libreoffice-gtk : Depends: libreoffice-core (= 1:5.1.2~rc2-0ubuntu1~trusty0) but it is not going to be installed
                   Recommends: libreoffice-style-breeze but it is not going to be installed or
                               libreoffice-style-tango but it is not going to be installed or
                               libreoffice-style-elementary but it is not going to be installed
 libreoffice-impress : Depends: libreoffice-core (= 1:5.1.2~rc2-0ubuntu1~trusty0) but it is not going to be installed
 libreoffice-math : Depends: libreoffice-core (= 1:5.1.2~rc2-0ubuntu1~trusty0) but it is not going to be installed
 libreoffice-pdfimport : Depends: libreoffice-core but it is not going to be installed
 libreoffice-report-builder-bin : Depends: libreoffice-core but it is not going to be installed
 libreoffice-sdbc-firebird : Depends: libreoffice-core but it is not going to be installed
 libreoffice-sdbc-hsqldb : Depends: libreoffice-core but it is not going to be installed
                           Depends: libreoffice-java-common (>= 1:5.1.2~rc2~) but it is not going to be installed
 libreoffice-writer : Depends: libreoffice-core (= 1:5.1.2~rc2-0ubuntu1~trusty0) but it is not going to be installed
 python3-uno : Depends: libreoffice-core (= 1:5.1.2~rc2-0ubuntu1~trusty0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by Nahua_Kang on 2016-04-17
With the information above, I did the following and still using ian-weisser's response on the previous post:
```

sudo apt-get autoremove openoffice-debian-menus libreoffice libreoffice-avmedia-backend-gstreamer libreoffice-core libreoffice-java-common libreoffice-ogltrans libreoffice-style-elementary libreoffice-style-galaxy libreoffice-style-human libreoffice-base libreoffice-base-core libreoffice-base-drivers libreoffice-calc libreoffice-draw libreoffice-gnome libreoffice-gtk libreoffice-impress libreoffice-math libreoffice-pdfimport libreoffice-report-builder-bin libreoffice-sdbc-firebird libreoffice-sdbc-hsqldb libreoffice-writer python3-uno

```

I get the following results:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libreoffice libreoffice-avmedia-backend-gstreamer libreoffice-base
  libreoffice-base-core libreoffice-base-drivers libreoffice-calc
  libreoffice-core libreoffice-draw libreoffice-gnome libreoffice-gtk
  libreoffice-impress libreoffice-java-common libreoffice-math
  libreoffice-ogltrans libreoffice-pdfimport libreoffice-report-builder-bin
  libreoffice-sdbc-firebird libreoffice-sdbc-hsqldb
  libreoffice-style-elementary libreoffice-style-galaxy
  libreoffice-style-human libreoffice-writer openoffice-debian-menus
  python3-uno
0 upgraded, 0 newly installed, 24 to remove and 0 not upgraded.
23 not fully installed or removed.
After this operation, 229 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 205200 files and directories currently installed.)
Removing libreoffice (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Removing libreoffice-avmedia-backend-gstreamer (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Removing libreoffice-report-builder-bin (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Removing libreoffice-base (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Removing 'diversion of /usr/lib/libreoffice/share/basic/dialog.xlc to /usr/lib/libreoffice/share/basic/dialog.xlc.noaccess by libreoffice-base'
Removing 'diversion of /usr/lib/libreoffice/share/basic/script.xlc to /usr/lib/libreoffice/share/basic/script.xlc.noaccess by libreoffice-base'
Removing libreoffice-calc (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Removing libreoffice-writer (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Removing libreoffice-base-core (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Removing libreoffice-base-drivers (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Removing libreoffice-sdbc-hsqldb (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Removing libreoffice-sdbc-firebird (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Removing libreoffice-core (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Removing libreoffice-ogltrans (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Removing libreoffice-impress (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Removing libreoffice-draw (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Removing libreoffice-gnome (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Removing libreoffice-gtk (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Removing libreoffice-java-common (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Removing libreoffice-math (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Removing libreoffice-pdfimport (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Removing libreoffice-style-elementary (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Removing libreoffice-style-human (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Removing libreoffice-style-galaxy (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Removing python3-uno (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Removing openoffice-debian-menus (4.1.2-9782) ...
/usr/bin/gtk-update-icon-cache
gtk-update-icon-cache: Cache file created successfully.
/usr/bin/gtk-update-icon-cache
gtk-update-icon-cache: Cache file created successfully.
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for gnome-icon-theme (3.10.0-0ubuntu2) ...

```

To see if the above actions succeeded, I tried again to remove openoffice-debian-menus:
```

kangnahua@kangnahua:~$ sudo apt-get autoremove openoffice-debian-menus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'openoffice-debian-menus' is not installed, so not removed
The following packages will be REMOVED:
  ca-certificates-java default-jre default-jre-headless java-common
  libatk-wrapper-java libatk-wrapper-java-jni libbonobo2-0 libbonobo2-common
  libgconf2-4 libgif4 libgnome2-0 libgnome2-bin libgnome2-common
  libgnomevfs2-0 libgnomevfs2-common libhsqldb1.8.0-java libidl-common libidl0
  liborbit-2-0 liborbit2 libsctp1 libservlet3.0-java lksctp-tools lp-solve
  openjdk-7-jre openjdk-7-jre-headless tzdata-java uno-libs3 ure
0 upgraded, 0 newly installed, 29 to remove and 0 not upgraded.
After this operation, 73.5 MB disk space will be freed.
Do you want to continue? [Y/n] 


```
Not sure if I should remove any of the above-mentioned things, so I said no as it seems I have uninstalled openoffice-debian-menus?
Also tried:
```

kangnahua@kangnahua:~$ sudo apt-get update
[sudo] password for kangnahua: 
Ign http://dl.google.com stable InRelease
Ign http://ch.archive.ubuntu.com trusty InRelease                              
Ign http://archive.canonical.com trusty InRelease                              
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://ch.archive.ubuntu.com trusty-updates InRelease                      
Hit http://ch.archive.ubuntu.com trusty-backports InRelease                    
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://dl.google.com stable Release.gpg                                    
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://ch.archive.ubuntu.com trusty Release.gpg                            
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://archive.canonical.com trusty Release                                
Hit http://dl.google.com stable Release                                        
Hit http://ch.archive.ubuntu.com trusty Release                                
Ign http://ppa.launchpad.net trusty Release.gpg                                
Ign http://ppa.launchpad.net trusty Release                                    
Hit http://ch.archive.ubuntu.com trusty-updates/main Sources                   
Hit http://ch.archive.ubuntu.com trusty-updates/restricted Sources             
Hit http://ch.archive.ubuntu.com trusty-updates/universe Sources               
Hit http://ch.archive.ubuntu.com trusty-updates/multiverse Sources             
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://ch.archive.ubuntu.com trusty-updates/main amd64 Packages            
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://ch.archive.ubuntu.com trusty-updates/restricted amd64 Packages      
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Ign http://linux.dropbox.com trusty InRelease                                  
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://ch.archive.ubuntu.com trusty-updates/universe amd64 Packages        
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://ch.archive.ubuntu.com trusty-updates/multiverse amd64 Packages      
Hit http://archive.canonical.com trusty/partner Translation-en                 
Hit http://ch.archive.ubuntu.com trusty-updates/main i386 Packages             
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ch.archive.ubuntu.com trusty-updates/restricted i386 Packages       
Hit http://ch.archive.ubuntu.com trusty-updates/universe i386 Packages         
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ch.archive.ubuntu.com trusty-updates/multiverse i386 Packages       
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ch.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://security.ubuntu.com trusty-security InRelease                       
Hit http://ch.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://linux.dropbox.com trusty Release.gpg                                
Hit http://ch.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://ch.archive.ubuntu.com trusty-updates/universe Translation-en        
Hit http://ch.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://ch.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://ch.archive.ubuntu.com trusty-backports/universe Sources             
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit http://ch.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://security.ubuntu.com trusty-security/main Sources                    
Hit http://ch.archive.ubuntu.com trusty-backports/main amd64 Packages          
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://ch.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Hit http://ch.archive.ubuntu.com trusty-backports/universe amd64 Packages      
Hit http://ch.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
Hit http://ch.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://ch.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://ch.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://ch.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://ch.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://security.ubuntu.com trusty-security/restricted Sources              
Hit http://ch.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://linux.dropbox.com trusty Release                                    
Hit http://ch.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://ch.archive.ubuntu.com trusty-backports/universe Translation-en      
Hit http://ch.archive.ubuntu.com trusty/main Sources                           
Hit http://ch.archive.ubuntu.com trusty/restricted Sources                     
Hit http://ch.archive.ubuntu.com trusty/universe Sources                       
Err http://ppa.launchpad.net trusty/main amd64 Packages                        
  404  Not Found
Hit http://security.ubuntu.com trusty-security/universe Sources                
Hit http://ch.archive.ubuntu.com trusty/multiverse Sources                     
Err http://ppa.launchpad.net trusty/main i386 Packages                         
  404  Not Found
Hit http://ch.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://ch.archive.ubuntu.com trusty/restricted amd64 Packages              
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Hit http://ch.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://ch.archive.ubuntu.com trusty/multiverse amd64 Packages              
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ch.archive.ubuntu.com trusty/main i386 Packages                     
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://ch.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://ch.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Hit http://ch.archive.ubuntu.com trusty/multiverse i386 Packages               
Ign http://dl.google.com stable/main Translation-en                            
Hit http://ch.archive.ubuntu.com trusty/main Translation-en                    
Hit http://ch.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Hit http://linux.dropbox.com trusty/main amd64 Packages                        
Hit http://ch.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://ch.archive.ubuntu.com trusty/universe Translation-en                
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Hit http://linux.dropbox.com trusty/main i386 Packages                         
Ign http://ch.archive.ubuntu.com trusty/main Translation-en_US                 
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages       
Ign http://ch.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://ch.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://ch.archive.ubuntu.com trusty/universe Translation-en_US             
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Hit http://security.ubuntu.com trusty-security/universe i386 Packages
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages
Hit http://security.ubuntu.com trusty-security/main Translation-en
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Ign http://linux.dropbox.com trusty/main Translation-en_US
Ign http://linux.dropbox.com trusty/main Translation-en
W: Failed to fetch http://ppa.launchpad.net/upubuntu-com/office/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/upubuntu-com/office/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

kangnahua@kangnahua:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  ca-certificates-java default-jre default-jre-headless java-common
  libatk-wrapper-java libatk-wrapper-java-jni libbonobo2-0 libbonobo2-common
  libgconf2-4 libgif4 libgnome2-0 libgnome2-bin libgnome2-common
  libgnomevfs2-0 libgnomevfs2-common libhsqldb1.8.0-java libidl-common libidl0
  liborbit-2-0 liborbit2 libsctp1 libservlet3.0-java lksctp-tools lp-solve
  openjdk-7-jre openjdk-7-jre-headless tzdata-java uno-libs3 ure
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```

---

### Post by Nahua_Kang on 2016-04-18
Since no one is helping, I assumed that my question is too simple and I went forward with installing LibreOffice again:
```

kangnahua@kangnahua:~$ sudo apt-get install libreoffice
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libreoffice-avmedia-backend-gstreamer libreoffice-base libreoffice-base-core
  libreoffice-base-drivers libreoffice-calc libreoffice-common
  libreoffice-core libreoffice-draw libreoffice-gnome libreoffice-gtk
  libreoffice-impress libreoffice-java-common libreoffice-math
  libreoffice-pdfimport libreoffice-report-builder-bin
  libreoffice-sdbc-firebird libreoffice-sdbc-hsqldb
  libreoffice-style-elementary libreoffice-style-galaxy libreoffice-writer
  python3-uno
Suggested packages:
  imagemagick graphicsmagick-imagemagick-compat libreoffice-grammarcheck
  libreoffice-help-5.1 libreoffice-l10n-5.1 mythes-thesaurus
  openclipart2-libreoffice openclipart-libreoffice pstoedit unixodbc
  libreoffice-officebean libreoffice-gcj libreoffice-report-builder
  libjtds-java libreoffice-mysql-connector libmyodbc libmysql-java
  libreoffice-sdbc-postgresql odbc-postgresql libpg-java libsqliteodbc tdsodbc
  mdbtools ocl-icd-libopencl1 libreoffice-style-breeze
  libreoffice-style-hicontrast libreoffice-style-human
  libreoffice-style-oxygen libreoffice-style-sifr libreoffice-style-tango
  libreoffice-evolution fonts-crosextra-caladea fonts-crosextra-carlito
The following NEW packages will be installed:
  libreoffice libreoffice-avmedia-backend-gstreamer libreoffice-base
  libreoffice-base-core libreoffice-base-drivers libreoffice-calc
  libreoffice-common libreoffice-core libreoffice-draw libreoffice-gnome
  libreoffice-gtk libreoffice-impress libreoffice-java-common libreoffice-math
  libreoffice-pdfimport libreoffice-report-builder-bin
  libreoffice-sdbc-firebird libreoffice-sdbc-hsqldb
  libreoffice-style-elementary libreoffice-style-galaxy libreoffice-writer
  python3-uno
0 upgraded, 22 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/81.5 MB of archives.
After this operation, 308 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Selecting previously unselected package libreoffice-style-galaxy.
(Reading database ... 204376 files and directories currently installed.)
Preparing to unpack .../libreoffice-style-galaxy_1%3a5.1.2~rc2-0ubuntu1~trusty0_all.deb ...
Unpacking libreoffice-style-galaxy (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Selecting previously unselected package libreoffice-style-elementary.
Preparing to unpack .../libreoffice-style-elementary_1%3a5.1.2~rc2-0ubuntu1~trusty0_all.deb ...
Unpacking libreoffice-style-elementary (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Preparing to unpack .../libreoffice-common_1%3a5.1.2~rc2-0ubuntu1~trusty0_all.deb ...
Unpacking libreoffice-common (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Selecting previously unselected package libreoffice-core.
Preparing to unpack .../libreoffice-core_1%3a5.1.2~rc2-0ubuntu1~trusty0_amd64.deb ...
Unpacking libreoffice-core (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Selecting previously unselected package libreoffice-base-core.
Preparing to unpack .../libreoffice-base-core_1%3a5.1.2~rc2-0ubuntu1~trusty0_amd64.deb ...
Unpacking libreoffice-base-core (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Selecting previously unselected package libreoffice-base-drivers.
Preparing to unpack .../libreoffice-base-drivers_1%3a5.1.2~rc2-0ubuntu1~trusty0_amd64.deb ...
Unpacking libreoffice-base-drivers (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Selecting previously unselected package libreoffice-base.
Preparing to unpack .../libreoffice-base_1%3a5.1.2~rc2-0ubuntu1~trusty0_amd64.deb ...
Adding 'diversion of /usr/lib/libreoffice/share/basic/dialog.xlc to /usr/lib/libreoffice/share/basic/dialog.xlc.noaccess by libreoffice-base'
Adding 'diversion of /usr/lib/libreoffice/share/basic/script.xlc to /usr/lib/libreoffice/share/basic/script.xlc.noaccess by libreoffice-base'
Unpacking libreoffice-base (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Selecting previously unselected package libreoffice-calc.
Preparing to unpack .../libreoffice-calc_1%3a5.1.2~rc2-0ubuntu1~trusty0_amd64.deb ...
Unpacking libreoffice-calc (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Selecting previously unselected package libreoffice-draw.
Preparing to unpack .../libreoffice-draw_1%3a5.1.2~rc2-0ubuntu1~trusty0_amd64.deb ...
Unpacking libreoffice-draw (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Selecting previously unselected package libreoffice-impress.
Preparing to unpack .../libreoffice-impress_1%3a5.1.2~rc2-0ubuntu1~trusty0_amd64.deb ...
Unpacking libreoffice-impress (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Selecting previously unselected package libreoffice-math.
Preparing to unpack .../libreoffice-math_1%3a5.1.2~rc2-0ubuntu1~trusty0_amd64.deb ...
Unpacking libreoffice-math (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Selecting previously unselected package libreoffice-report-builder-bin.
Preparing to unpack .../libreoffice-report-builder-bin_1%3a5.1.2~rc2-0ubuntu1~trusty0_amd64.deb ...
Unpacking libreoffice-report-builder-bin (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Selecting previously unselected package libreoffice-writer.
Preparing to unpack .../libreoffice-writer_1%3a5.1.2~rc2-0ubuntu1~trusty0_amd64.deb ...
Unpacking libreoffice-writer (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Selecting previously unselected package libreoffice-avmedia-backend-gstreamer.
Preparing to unpack .../libreoffice-avmedia-backend-gstreamer_1%3a5.1.2~rc2-0ubuntu1~trusty0_amd64.deb ...
Unpacking libreoffice-avmedia-backend-gstreamer (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Selecting previously unselected package libreoffice-java-common.
Preparing to unpack .../libreoffice-java-common_1%3a5.1.2~rc2-0ubuntu1~trusty0_all.deb ...
Unpacking libreoffice-java-common (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Selecting previously unselected package python3-uno.
Preparing to unpack .../python3-uno_1%3a5.1.2~rc2-0ubuntu1~trusty0_amd64.deb ...
Unpacking python3-uno (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Selecting previously unselected package libreoffice.
Preparing to unpack .../libreoffice_1%3a5.1.2~rc2-0ubuntu1~trusty0_amd64.deb ...
Unpacking libreoffice (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Selecting previously unselected package libreoffice-gtk.
Preparing to unpack .../libreoffice-gtk_1%3a5.1.2~rc2-0ubuntu1~trusty0_amd64.deb ...
Unpacking libreoffice-gtk (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Selecting previously unselected package libreoffice-gnome.
Preparing to unpack .../libreoffice-gnome_1%3a5.1.2~rc2-0ubuntu1~trusty0_amd64.deb ...
Unpacking libreoffice-gnome (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Selecting previously unselected package libreoffice-sdbc-firebird.
Preparing to unpack .../libreoffice-sdbc-firebird_1%3a5.1.2~rc2-0ubuntu1~trusty0_amd64.deb ...
Unpacking libreoffice-sdbc-firebird (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Selecting previously unselected package libreoffice-sdbc-hsqldb.
Preparing to unpack .../libreoffice-sdbc-hsqldb_1%3a5.1.2~rc2-0ubuntu1~trusty0_amd64.deb ...
Unpacking libreoffice-sdbc-hsqldb (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Selecting previously unselected package libreoffice-pdfimport.
Preparing to unpack .../libreoffice-pdfimport_1%3a5.1.2~rc2-0ubuntu1~trusty0_amd64.deb ...
Unpacking libreoffice-pdfimport (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Processing triggers for gnome-icon-theme (3.10.0-0ubuntu2) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up libreoffice-common (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Installing new version of config file /etc/bash_completion.d/libreoffice.sh ...
Installing new version of config file /etc/libreoffice/sofficerc ...
Installing new version of config file /etc/libreoffice/psprint.conf ...
Setting up libreoffice-style-galaxy (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Setting up libreoffice-style-elementary (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Setting up libreoffice-core (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Setting up libreoffice-base-core (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Setting up libreoffice-base-drivers (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Setting up libreoffice-base (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Setting up libreoffice-calc (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Setting up libreoffice-draw (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Setting up libreoffice-impress (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Setting up libreoffice-math (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Setting up libreoffice-report-builder-bin (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Setting up libreoffice-writer (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Setting up libreoffice-avmedia-backend-gstreamer (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Setting up libreoffice-java-common (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Setting up python3-uno (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Setting up libreoffice (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Setting up libreoffice-gtk (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Setting up libreoffice-gnome (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Setting up libreoffice-sdbc-firebird (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Setting up libreoffice-sdbc-hsqldb (1:5.1.2~rc2-0ubuntu1~trusty0) ...
Setting up libreoffice-pdfimport (1:5.1.2~rc2-0ubuntu1~trusty0) ...

```
Seems rather successful.

---

### Post by ian-weisser on 2016-04-18
> **Nahua_Kang said:**
> Since no one is helping

Be nice. We don't work for you nor owe you anything.
We are fellow Ubuntu participants who like to help.

Good etiquite in this forum is to bump ater 12 hours or so, or to retitle your thread.

---

