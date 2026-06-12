---
title: "problam after new install of ubuntu 15.04"
date: 2015-07-10
forum: General Help
---

### Post by offir on 2015-07-10
i am trying to remove a program (any program)  from the "ubuntu program manager"
and i get this error

same error i get after try to install java


i try servel way to fix this but it did not work 

try to add a new ppa
or 
```
sudo apt-get purge openjdk*
```
but no go

evrything i want to install i get this messege 

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
(Reading database ... 192907 files and directories currently installed.)
Removing gufw (15.04.0-0ubuntu1) ...
Removing gnome-icon-theme-symbolic (3.12.0-1) ...
Removing python-netifaces (0.10.4-0.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu5) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Processing triggers for bamfdaemon (0.5.1+15.04.20150202-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.58ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.14-0ubuntu1) ...
Processing triggers for man-db (2.7.0.2-5) ...
Processing triggers for gnome-icon-theme (3.12.0-1ubuntu1) ...
Setting up oracle-java7-installer (7u80+7u60arm-0~webupd8~1) ...
Downloading Oracle Java 7...
--2015-07-10 20:40:50--  http://download.oracle.com/otn-pub/java/jdk/7u80-b15/jdk-7u80-linux-x64.tar.gz
Resolving download.oracle.com (download.oracle.com)... 212.143.162.211, 212.143.162.203
Connecting to download.oracle.com (download.oracle.com)|212.143.162.211|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/jdk/7u80-b15/jdk-7u80-linux-x64.tar.gz [following]
--2015-07-10 20:40:50--  https://edelivery.oracle.com/otn-pub/java/jdk/7u80-b15/jdk-7u80-linux-x64.tar.gz
Resolving edelivery.oracle.com (edelivery.oracle.com)... 23.44.246.140
Connecting to edelivery.oracle.com (edelivery.oracle.com)|23.44.246.140|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://download.oracle.com/otn-pub/java/jdk/7u80-b15/jdk-7u80-linux-x64.tar.gz?AuthParam=1436550170_cc2e58d2bad738a8bc3c387d655311c6 [following]
--2015-07-10 20:40:51--  http://download.oracle.com/otn-pub/java/jdk/7u80-b15/jdk-7u80-linux-x64.tar.gz?AuthParam=1436550170_cc2e58d2bad738a8bc3c387d655311c6
Connecting to download.oracle.com (download.oracle.com)|212.143.162.211|:80... connected.
HTTP request sent, awaiting response... 403 Forbidden
2015-07-10 20:40:53 ERROR 403: Forbidden.

download failed
Oracle JDK 7 is NOT installed.
dpkg: error processing package oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java7-installer
Error in function: 
Setting up oracle-java7-installer (7u80+7u60arm-0~webupd8~1) ...
Downloading Oracle Java 7...
--2015-07-10 20:40:56--  http://download.oracle.com/otn-pub/java/jdk/7u80-b15/jdk-7u80-linux-x64.tar.gz
Resolving download.oracle.com (download.oracle.com)... 212.143.162.203, 212.143.162.211
Connecting to download.oracle.com (download.oracle.com)|212.143.162.203|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/jdk/7u80-b15/jdk-7u80-linux-x64.tar.gz [following]
--2015-07-10 20:40:56--  https://edelivery.oracle.com/otn-pub/java/jdk/7u80-b15/jdk-7u80-linux-x64.tar.gz
Resolving edelivery.oracle.com (edelivery.oracle.com)... 23.44.246.140
Connecting to edelivery.oracle.com (edelivery.oracle.com)|23.44.246.140|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://download.oracle.com/otn-pub/java/jdk/7u80-b15/jdk-7u80-linux-x64.tar.gz?AuthParam=1436550176_d5fd15b91f5f3c11c3386b8283dc0428 [following]
--2015-07-10 20:40:57--  http://download.oracle.com/otn-pub/java/jdk/7u80-b15/jdk-7u80-linux-x64.tar.gz?AuthParam=1436550176_d5fd15b91f5f3c11c3386b8283dc0428
Connecting to download.oracle.com (download.oracle.com)|212.143.162.203|:80... connected.
HTTP request sent, awaiting response... 403 Forbidden
2015-07-10 20:40:59 ERROR 403: Forbidden.

download failed
Oracle JDK 7 is NOT installed.
dpkg: error processing package oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1

```

---

### Post by Vladlenin5000 on 2015-07-10
Please do a full update and post the error messages (if any):
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by offir on 2015-07-11
in The first command, nothing happened 
it work with no problam

```
Ign http://il.archive.ubuntu.com vivid InRelease
Ign http://il.archive.ubuntu.com vivid-updates InRelease                       
Ign http://security.ubuntu.com vivid-security InRelease                        
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://il.archive.ubuntu.com vivid-backports InRelease                     
Hit http://il.archive.ubuntu.com vivid Release.gpg                             
Get:1 http://security.ubuntu.com vivid-security Release.gpg [933 B]            
Ign http://archive.canonical.com vivid InRelease                               
Get:2 http://il.archive.ubuntu.com vivid-updates Release.gpg [933 B]           
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://il.archive.ubuntu.com vivid-backports Release.gpg                   
Get:3 http://security.ubuntu.com vivid-security Release [63.5 kB]              
Hit http://il.archive.ubuntu.com vivid Release                                 
Hit http://archive.canonical.com vivid Release.gpg                             
Get:4 http://il.archive.ubuntu.com vivid-updates Release [63.5 kB]             
Hit http://archive.canonical.com vivid Release                                 
Ign http://ppa.launchpad.net vivid InRelease                                   
Hit http://il.archive.ubuntu.com vivid-backports Release                       
Hit http://archive.canonical.com vivid/partner Sources                                                                                     
Hit http://il.archive.ubuntu.com vivid/main Sources                                                                                        
Get:5 http://security.ubuntu.com vivid-security/main Sources [26.4 kB]                                                                     
Hit http://il.archive.ubuntu.com vivid/restricted Sources                                                                                  
Ign http://ppa.launchpad.net trusty InRelease                                                                                              
Hit http://il.archive.ubuntu.com vivid/universe Sources                                                                                    
Hit http://archive.canonical.com vivid/partner amd64 Packages                                                                              
Get:6 http://security.ubuntu.com vivid-security/restricted Sources [28 B]                                                                  
Hit http://il.archive.ubuntu.com vivid/multiverse Sources                                                                                  
Hit http://il.archive.ubuntu.com vivid/main amd64 Packages                                                                                 
Hit http://download.mono-project.com wheezy InRelease                                                                                      
Hit http://archive.canonical.com vivid/partner i386 Packages                                                                        
Get:7 http://security.ubuntu.com vivid-security/universe Sources [12.3 kB]                                                                 
Ign http://ppa.launchpad.net trusty InRelease                                                                                              
Hit http://il.archive.ubuntu.com vivid/restricted amd64 Packages                                                                           
Hit http://download.mono-project.com wheezy-apache24-compat InRelease                                                                 
Hit http://archive.canonical.com vivid/partner Translation-en                                                                         
Hit http://il.archive.ubuntu.com vivid/universe amd64 Packages                                                                             
Hit http://download.mono-project.com wheezy/main amd64 Packages                                                                            
Hit http://il.archive.ubuntu.com vivid/multiverse amd64 Packages                                                                           
Get:8 http://security.ubuntu.com vivid-security/multiverse Sources [1,955 B]                                                               
Hit http://download.mono-project.com wheezy/main i386 Packages                                                                             
Hit http://archive.getdeb.net trusty-getdeb InRelease                                                                                      
Hit http://il.archive.ubuntu.com vivid/main i386 Packages                                                                                  
Ign http://ppa.launchpad.net trusty InRelease                                                                                              
Get:9 http://security.ubuntu.com vivid-security/main amd64 Packages [80.6 kB]                                                              
Hit http://il.archive.ubuntu.com vivid/restricted i386 Packages                                                                            
Hit http://il.archive.ubuntu.com vivid/universe i386 Packages                                                                              
Hit http://il.archive.ubuntu.com vivid/multiverse i386 Packages                                                                            
Get:10 http://security.ubuntu.com vivid-security/restricted amd64 Packages [28 B]                                                          
Hit http://il.archive.ubuntu.com vivid/main Translation-en                                                                                 
Get:11 http://security.ubuntu.com vivid-security/universe amd64 Packages [38.9 kB]                                                         
Ign http://ppa.launchpad.net trusty InRelease                                                                                              
Hit http://il.archive.ubuntu.com vivid/multiverse Translation-en                                                                           
Hit http://il.archive.ubuntu.com vivid/restricted Translation-en                                                                           
Hit http://il.archive.ubuntu.com vivid/universe Translation-en                                                                             
Hit http://archive.getdeb.net trusty-getdeb/games amd64 Packages                                                                           
Get:12 http://security.ubuntu.com vivid-security/multiverse amd64 Packages [3,492 B]                                                       
Get:13 http://il.archive.ubuntu.com vivid-updates/main Sources [59.1 kB]                                                                   
Ign http://ppa.launchpad.net trusty InRelease                                                                                              
Get:14 http://security.ubuntu.com vivid-security/main i386 Packages [79.9 kB]                                                              
Get:15 http://il.archive.ubuntu.com vivid-updates/restricted Sources [28 B]                                                                
Get:16 http://il.archive.ubuntu.com vivid-updates/universe Sources [26.7 kB]                                                               
Hit http://download.mono-project.com wheezy-apache24-compat/main amd64 Packages                                                            
Hit http://archive.getdeb.net trusty-getdeb/games i386 Packages                                                                            
Hit http://download.mono-project.com wheezy-apache24-compat/main i386 Packages                                                             
Get:17 http://il.archive.ubuntu.com vivid-updates/multiverse Sources [1,955 B]                                                             
Ign http://ppa.launchpad.net vivid InRelease                                                                                              
Get:18 http://il.archive.ubuntu.com vivid-updates/main amd64 Packages [138 kB]                                                             
Get:19 http://security.ubuntu.com vivid-security/restricted i386 Packages [28 B]                                                           
Get:20 http://security.ubuntu.com vivid-security/universe i386 Packages [38.9 kB]                                                          
Get:21 http://il.archive.ubuntu.com vivid-updates/restricted amd64 Packages [28 B]                                                         
Get:22 http://il.archive.ubuntu.com vivid-updates/universe amd64 Packages [77.0 kB]                                                        
Get:23 http://security.ubuntu.com vivid-security/multiverse i386 Packages [3,673 B]                                                        
Get:24 http://il.archive.ubuntu.com vivid-updates/multiverse amd64 Packages [3,492 B]                                                      
Hit http://security.ubuntu.com vivid-security/main Translation-en                                                                          
Hit http://security.ubuntu.com vivid-security/multiverse Translation-en                                                                    
Get:25 http://il.archive.ubuntu.com vivid-updates/main i386 Packages [135 kB]                                                              
Hit http://security.ubuntu.com vivid-security/restricted Translation-en                                                                    
Get:26 http://il.archive.ubuntu.com vivid-updates/restricted i386 Packages [28 B]                                                          
Ign http://ppa.launchpad.net trusty InRelease                                                                                              
Hit http://security.ubuntu.com vivid-security/universe Translation-en                                                                      
Get:27 http://il.archive.ubuntu.com vivid-updates/universe i386 Packages [77.1 kB]                                                         
Get:28 http://il.archive.ubuntu.com vivid-updates/multiverse i386 Packages [3,673 B]                                                       
Hit http://il.archive.ubuntu.com vivid-updates/main Translation-en                                                                         
Hit http://il.archive.ubuntu.com vivid-updates/multiverse Translation-en                                                                   
Hit http://il.archive.ubuntu.com vivid-updates/restricted Translation-en                                                                   
Hit http://il.archive.ubuntu.com vivid-updates/universe Translation-en                                                                     
Ign http://ppa.launchpad.net trusty InRelease                                                                                              
Hit http://il.archive.ubuntu.com vivid-backports/main Sources                                                                              
Hit http://il.archive.ubuntu.com vivid-backports/restricted Sources                                                                        
Hit http://il.archive.ubuntu.com vivid-backports/universe Sources                                                                          
Hit http://il.archive.ubuntu.com vivid-backports/multiverse Sources                                                                        
Hit http://il.archive.ubuntu.com vivid-backports/main amd64 Packages                                                                       
Hit http://il.archive.ubuntu.com vivid-backports/restricted amd64 Packages                                                                 
Hit http://il.archive.ubuntu.com vivid-backports/universe amd64 Packages                                                                   
Hit http://il.archive.ubuntu.com vivid-backports/multiverse amd64 Packages                                                                 
Ign http://ppa.launchpad.net vivid InRelease                                                                                               
Hit http://il.archive.ubuntu.com vivid-backports/main i386 Packages                                                                        
Hit http://il.archive.ubuntu.com vivid-backports/restricted i386 Packages                                                                  
Hit http://ppa.launchpad.net trusty Release.gpg                                                                                            
Hit http://il.archive.ubuntu.com vivid-backports/universe i386 Packages                                                                    
Hit http://il.archive.ubuntu.com vivid-backports/multiverse i386 Packages                                                                  
Hit http://ppa.launchpad.net trusty Release.gpg                                                                                            
Hit http://il.archive.ubuntu.com vivid-backports/main Translation-en                                                                       
Hit http://il.archive.ubuntu.com vivid-backports/multiverse Translation-en                                                                 
Hit http://ppa.launchpad.net vivid Release.gpg                                                                                             
Hit http://il.archive.ubuntu.com vivid-backports/restricted Translation-en                                                                 
Hit http://il.archive.ubuntu.com vivid-backports/universe Translation-en                                                                   
Hit http://ppa.launchpad.net trusty Release.gpg                                                                                            
Hit http://ppa.launchpad.net trusty Release.gpg                                                                                            
Hit http://ppa.launchpad.net trusty Release.gpg                                                                                            
Hit http://ppa.launchpad.net trusty Release.gpg                                                                                            
Hit http://ppa.launchpad.net trusty Release.gpg                                                                                            
Hit http://ppa.launchpad.net vivid Release.gpg                                                                                             
Ign http://archive.getdeb.net trusty-getdeb/games Translation-en_US                                                                        
Hit http://ppa.launchpad.net trusty Release.gpg                                                                                            
Hit http://ppa.launchpad.net trusty Release.gpg                                                                                            
Ign http://archive.getdeb.net trusty-getdeb/games Translation-en                                                                           
Hit http://ppa.launchpad.net vivid Release.gpg                                                                                             
Hit http://ppa.launchpad.net trusty Release                                                                                                
Hit http://ppa.launchpad.net trusty Release                                                                                                
Hit http://ppa.launchpad.net vivid Release                                                                                                 
Hit http://ppa.launchpad.net trusty Release                                                                                                
Ign http://download.mono-project.com wheezy/main Translation-en_US                                                                         
Hit http://ppa.launchpad.net trusty Release                                                                                                
Ign http://download.mono-project.com wheezy/main Translation-en                                                                            
Hit http://ppa.launchpad.net trusty Release                                                                                                
Ign http://download.mono-project.com wheezy-apache24-compat/main Translation-en_US                                                         
Hit http://ppa.launchpad.net trusty Release                                                                                                
Ign http://download.mono-project.com wheezy-apache24-compat/main Translation-en                                                            
Hit http://ppa.launchpad.net trusty Release                                                                                                
Hit http://ppa.launchpad.net vivid Release                                                                                                 
Hit http://ppa.launchpad.net trusty Release                                                                                                
Hit http://ppa.launchpad.net trusty Release                                                                                                
Hit http://ppa.launchpad.net vivid Release                                                                                                 
Hit http://ppa.launchpad.net trusty/main amd64 Packages                                                                                    
Hit http://ppa.launchpad.net trusty/main i386 Packages                                                                                     
Hit http://ppa.launchpad.net trusty/main Translation-en                                                                                    
Hit http://ppa.launchpad.net trusty/main amd64 Packages                                                                                    
Hit http://ppa.launchpad.net trusty/main i386 Packages                                                                                     
Hit http://ppa.launchpad.net trusty/main Translation-en                                                                                    
Hit http://ppa.launchpad.net vivid/main amd64 Packages                                                                                     
Hit http://ppa.launchpad.net vivid/main i386 Packages                                                                                      
Hit http://ppa.launchpad.net vivid/main Translation-en                                                                                     
Hit http://ppa.launchpad.net trusty/main Sources                                                                                           
Hit http://ppa.launchpad.net trusty/main amd64 Packages                                                                                    
Hit http://ppa.launchpad.net trusty/main i386 Packages                                                                                     
Hit http://ppa.launchpad.net trusty/main Translation-en                                                                                    
Hit http://ppa.launchpad.net trusty/main amd64 Packages                                                                                    
Hit http://ppa.launchpad.net trusty/main i386 Packages                                                                                     
Hit http://ppa.launchpad.net trusty/main Translation-en                                                                                    
Hit http://ppa.launchpad.net trusty/main amd64 Packages                                                                                    
Hit http://ppa.launchpad.net trusty/main i386 Packages                                                                                     
Hit http://ppa.launchpad.net trusty/main Translation-en                                                                                    
Hit http://ppa.launchpad.net trusty/main amd64 Packages                                                                                    
Hit http://ppa.launchpad.net trusty/main i386 Packages                                                                                     
Hit http://ppa.launchpad.net trusty/main Translation-en                                                                                    
Hit http://ppa.launchpad.net trusty/main amd64 Packages                                                                                    
Hit http://ppa.launchpad.net trusty/main i386 Packages                                                                                     
Hit http://ppa.launchpad.net trusty/main Translation-en                                                                                    
Hit http://ppa.launchpad.net vivid/main amd64 Packages                                                                                     
Hit http://ppa.launchpad.net vivid/main i386 Packages                                                                                      
Hit http://ppa.launchpad.net vivid/main Translation-en                                                                                     
Hit http://ppa.launchpad.net trusty/main amd64 Packages                                                                                    
Hit http://ppa.launchpad.net trusty/main i386 Packages                                                                                     
Hit http://ppa.launchpad.net trusty/main Sources                                                                                           
Hit http://ppa.launchpad.net trusty/main amd64 Packages                                                                                    
Hit http://ppa.launchpad.net trusty/main i386 Packages                                                                                     
Hit http://ppa.launchpad.net trusty/main Translation-en                                                                                    
Hit http://ppa.launchpad.net vivid/main amd64 Packages                                                                                     
Hit http://ppa.launchpad.net vivid/main i386 Packages                                                                                      
Hit http://ppa.launchpad.net vivid/main Translation-en                                                                                     
Ign http://ppa.launchpad.net trusty/main Translation-en_US                                                                                 
Ign http://ppa.launchpad.net trusty/main Translation-en                                                                                    
Fetched 938 kB in 39s (23.5 kB/s)                                                                                                          
Reading package lists... Done
```


in The second and third commands were error messages

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... The following package was automatically installed and is no longer required:
  linux-image-generic
Use 'apt-get autoremove' to remove it.
Done
The following packages have been kept back:
  qbittorrent
The following packages will be upgraded:
  gimp-gmic gimp-plugin-registry ubuntu-tweak xserver-xorg-input-wacom
4 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 3,867 kB of archives.
After this operation, 1,872 kB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 http://il.archive.ubuntu.com/ubuntu/ vivid-updates/main xserver-xorg-input-wacom amd64 1:0.25.0-0ubuntu1.1 [83.2 kB]
Get:2 http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu/ trusty/main gimp-gmic amd64 1:1.6.5.0a-0trusty0~ppa [1,810 kB]
Get:3 http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu/ trusty/main gimp-plugin-registry amd64 7.20141204-0trusty0~ppa [1,400 kB]
Get:4 http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ trusty/main ubuntu-tweak all 0.8.8-1~trusty1 [573 kB]
Fetched 3,867 kB in 6s (637 kB/s)                                                                                                          
(Reading database ... 192089 files and directories currently installed.)
Preparing to unpack .../gimp-gmic_1%3a1.6.5.0a-0trusty0~ppa_amd64.deb ...
Unpacking gimp-gmic (1:1.6.5.0a-0trusty0~ppa) over (1.6.0.1-1) ...
Preparing to unpack .../gimp-plugin-registry_7.20141204-0trusty0~ppa_amd64.deb ...
Unpacking gimp-plugin-registry (7.20141204-0trusty0~ppa) over (7.20140602ubuntu1) ...
Preparing to unpack .../ubuntu-tweak_0.8.8-1~trusty1_all.deb ...
Unpacking ubuntu-tweak (0.8.8-1~trusty1) over (0.8.7-1~trusty2) ...
Preparing to unpack .../xserver-xorg-input-wacom_1%3a0.25.0-0ubuntu1.1_amd64.deb ...
Unpacking xserver-xorg-input-wacom (1:0.25.0-0ubuntu1.1) over (1:0.25.0-0ubuntu1) ...
Processing triggers for dbus (1.8.12-1ubuntu5) ...
Processing triggers for hicolor-icon-theme (0.14-0ubuntu1) ...
Processing triggers for gconf2 (3.2.6-3ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.44.1-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu5) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Processing triggers for bamfdaemon (0.5.1+15.04.20150202-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.58ubuntu1) ...
Processing triggers for man-db (2.7.0.2-5) ...
Setting up oracle-java7-installer (7u80+7u60arm-0~webupd8~1) ...
Downloading Oracle Java 7...
--2015-07-11 07:15:23--  http://download.oracle.com/otn-pub/java/jdk/7u80-b15/jdk-7u80-linux-x64.tar.gz
Resolving download.oracle.com (download.oracle.com)... 212.143.162.203, 212.143.162.211
Connecting to download.oracle.com (download.oracle.com)|212.143.162.203|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/jdk/7u80-b15/jdk-7u80-linux-x64.tar.gz [following]
--2015-07-11 07:15:23--  https://edelivery.oracle.com/otn-pub/java/jdk/7u80-b15/jdk-7u80-linux-x64.tar.gz
Resolving edelivery.oracle.com (edelivery.oracle.com)... 23.44.246.140
Connecting to edelivery.oracle.com (edelivery.oracle.com)|23.44.246.140|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://download.oracle.com/otn-pub/java/jdk/7u80-b15/jdk-7u80-linux-x64.tar.gz?AuthParam=1436588244_70f470c9c7ee4636e002ad7600f37c6a [following]
--2015-07-11 07:15:24--  http://download.oracle.com/otn-pub/java/jdk/7u80-b15/jdk-7u80-linux-x64.tar.gz?AuthParam=1436588244_70f470c9c7ee4636e002ad7600f37c6a
Connecting to download.oracle.com (download.oracle.com)|212.143.162.203|:80... connected.
HTTP request sent, awaiting response... 403 Forbidden
2015-07-11 07:15:33 ERROR 403: Forbidden.

download failed
Oracle JDK 7 is NOT installed.
dpkg: error processing package oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up gimp-gmic (1:1.6.5.0a-0trusty0~ppa) ...
Setting up gimp-plugin-registry (7.20141204-0trusty0~ppa) ...
Setting up ubuntu-tweak (0.8.8-1~trusty1) ...
Setting up xserver-xorg-input-wacom (1:0.25.0-0ubuntu1.1) ...
Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... The following package was automatically installed and is no longer required:
  linux-image-generic
Use 'apt-get autoremove' to remove it.
Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up oracle-java7-installer (7u80+7u60arm-0~webupd8~1) ...
Downloading Oracle Java 7...
--2015-07-11 07:15:51--  http://download.oracle.com/otn-pub/java/jdk/7u80-b15/jdk-7u80-linux-x64.tar.gz
Resolving download.oracle.com (download.oracle.com)... 212.143.162.203, 212.143.162.211
Connecting to download.oracle.com (download.oracle.com)|212.143.162.203|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/jdk/7u80-b15/jdk-7u80-linux-x64.tar.gz [following]
--2015-07-11 07:15:51--  https://edelivery.oracle.com/otn-pub/java/jdk/7u80-b15/jdk-7u80-linux-x64.tar.gz
Resolving edelivery.oracle.com (edelivery.oracle.com)... 23.44.246.140
Connecting to edelivery.oracle.com (edelivery.oracle.com)|23.44.246.140|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://download.oracle.com/otn-pub/java/jdk/7u80-b15/jdk-7u80-linux-x64.tar.gz?AuthParam=1436588273_5d6c759d136f7bc409eee57904e538a8 [following]
--2015-07-11 07:15:53--  http://download.oracle.com/otn-pub/java/jdk/7u80-b15/jdk-7u80-linux-x64.tar.gz?AuthParam=1436588273_5d6c759d136f7bc409eee57904e538a8
Connecting to download.oracle.com (download.oracle.com)|212.143.162.203|:80... connected.
HTTP request sent, awaiting response... 403 Forbidden
2015-07-11 07:15:56 ERROR 403: Forbidden.

download failed
Oracle JDK 7 is NOT installed.
dpkg: error processing package oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


also i got this Message

---

### Post by Bucky Ball on 2015-07-11
Just hit close on your screenshot, let the rest of the updates happen and, as the window says, the corefonts will be installed later without you needing to do anything.

---

### Post by offir on 2015-07-11
it is not working

every thing i want to install or remove give me error massge

---

### Post by offir on 2015-07-11
is there a way to make the computer stop try to install java
delete all that wait for install or smoething like that ?

---

### Post by Vladlenin5000 on 2015-07-11
At the moment you have two unrelated issues. Unrelated but the common denominator could be an internet connection problem...

**1. Microsoft TrueType fonts installer**. This is part of many software packages (WINE, Ubuntu Restricted Extras, etc.). The error you're experiencing is because you didn't accept the EULA when you first installed it as part of one of the aforementioned packages. You MAY not have had the chance to accept it due to an old bug, so I'm definitely NOT saying it's your fault. And it's easy to solve anyway, just remove/purge and reinstall. Use the terminal for guaranteed results:
```
sudo apt-get remove --purge ttf-mscorefonts-installer
sudo apt-get install ttf-mscorefonts-installer
```
At this time you'll notice the EULA. Use TAB and the arrow keys to navigate the options and ENTER to accept.

**2. Oracle Java 7.** This isn't standard so you must have explicitly told the system install it. Whatever the issue you're experiencing now it probably stems from the method you used to install it. So, this one is/was caused by you (probably).
Anyway, in order to correct it I suggest - again - removing/purging and reinstalling:
```
sudo apt-get remove --purge oracle-java7-installer
```
Then you can reinstall via a PPA.

For [Oracle Java 7]("http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html")
For [Oracle Java 8]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html") (recommended, unless you specifically need version 7)

---

### Post by offir on 2015-07-11
It semi-worked
I think


No more the  java message
Have not yet tried to install

I tried to install first  ttf-mscorefonts-installer
I received the message (EULA) asking
If I confirm
I clicked on OK
Then Yes

Then installation begins to download files
And could not download something


```
[COLOR="#0000FF"]offir@offir-vivid:~$[/COLOR] sudo apt-get remove --purge ttf-mscorefonts-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  linux-image-generic
Use 'apt-get autoremove' to remove it.
The following packages will be REMOVED:
  ttf-mscorefonts-installer*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 134 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 192062 files and directories currently installed.)
Removing ttf-mscorefonts-installer (3.4+nmu1ubuntu2) ...
Purging configuration files for ttf-mscorefonts-installer (3.4+nmu1ubuntu2) ...
Processing triggers for update-notifier-common (3.160) ...
[COLOR="#0000FF"]offir@offir-vivid:~$[/COLOR] sudo apt-get install ttf-mscorefonts-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  linux-image-generic
Use 'apt-get autoremove' to remove it.
The following NEW packages will be installed:
  ttf-mscorefonts-installer
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 29.5 kB of archives.
After this operation, 134 kB of additional disk space will be used.
Get:1 http://il.archive.ubuntu.com/ubuntu/ vivid/multiverse ttf-mscorefonts-installer all 3.4+nmu1ubuntu2 [29.5 kB]
Fetched 29.5 kB in 0s (828 kB/s)               
Preconfiguring packages ...
Selecting previously unselected package ttf-mscorefonts-installer.
(Reading database ... 192054 files and directories currently installed.)
Preparing to unpack .../ttf-mscorefonts-installer_3.4+nmu1ubuntu2_all.deb ...
Unpacking ttf-mscorefonts-installer (3.4+nmu1ubuntu2) ...
Processing triggers for fontconfig (2.11.1-0ubuntu6) ...
Processing triggers for update-notifier-common (3.160) ...
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/andale32.exe
Get:1 http://downloads.sourceforge.net/corefonts/andale32.exe [198 kB]
Fetched 198 kB in 0s (207 kB/s)                                                
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/arial32.exe
Get:1 http://downloads.sourceforge.net/corefonts/arial32.exe [554 kB]
Fetched 554 kB in 0s (692 kB/s)                                                
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/arialb32.exe
Get:1 http://downloads.sourceforge.net/corefonts/arialb32.exe [168 kB]
Fetched 168 kB in 0s (225 kB/s)                                                
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/comic32.exe
Err http://downloads.sourceforge.net/corefonts/comic32.exe
  403  Forbidden [IP: 193.206.140.34 80]
E: Failed to fetch http://downloads.sourceforge.net/corefonts/comic32.exe  403  Forbidden [IP: 193.206.140.34 80]

E: Download Failed
Setting up ttf-mscorefonts-installer (3.4+nmu1ubuntu2) .
```




> Then you can reinstall via a PPA.

For Oracle Java 7
For Oracle Java 8 (recommended, unless you specifically need version 7) 

is this good[COLOR="#FF0000"] ?[/COLOR]

```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
```

---

### Post by offir on 2015-07-12
Updated
After several attempts
I noticed that the installation is trying to download EXE files

I know
Firewall blocks this kind of file

I connected directly to the network (Different device)
No through the firewall 

And Typed the commands
And have worked

It's a little weird
Because I had no problem in three other computers 
ubuntu 12.04
ubuntu 12.04
ubuntu 14.04



as for the java 
i Typed 
```
sudo apt-get install oracle-java8-installer
```

and i got this 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
oracle-java8-installer is already the newest version.
The following package was automatically installed and is no longer required:
  linux-image-generic
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

is it ok[COLOR="#FF0000"] ?[/COLOR]

---

### Post by Vladlenin5000 on 2015-07-12
Here's the common denominator I mentioned before... ;-)

---

### Post by offir on 2015-07-12
I simply tried it
I did not think it would work

In three other computers there is no problem

As I said
Weird

---

