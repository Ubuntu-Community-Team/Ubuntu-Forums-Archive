---
title: "Package System is Broken, -f install doesn't work"
date: 2014-01-01
forum: General Help
---

### Post by xierdudeC on 2014-01-01
Hello,
The Ubuntu Software Center gives me "Packages cannot be installed or removed until the package system is repaired", but when I click "repair" it didn't work. I did sudo apt-get update and then sudo apt-get -f install but it didn't work.
When I try to install programs I get this:
```
The following packages have unmet dependencies:

mysql-server-5.5: PreDepends: mysql-common (>= 5.5.24-0ubuntu0.12.04.1) but 5.5.34-0ubuntu0.12.04.1 is installed
                  Depends: mysql-client-5.5 (>= 5.5.24-0ubuntu0.12.04.1) but 5.5.34-0ubuntu0.12.04.1 is installed
                  Depends: perl (>= 5.6) but 5.14.2-6ubuntu2.3 is installed
                  Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu4 is installed
                  Depends: upstart-job but it is a virtual package
                  Depends: mysql-server-core-5.5 (= 5.5.24-0ubuntu0.12.04.1) but 5.5.34-0ubuntu0.12.04.1 is installed



```Here's what I got after apt-get update:
```
elliot@ubuntu:~$ sudo apt-get updatesudo: /var/lib/sudo writable by non-owner (040770), should be mode 0700
[sudo] password for elliot: 
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg                 
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                    
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release             
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                     
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [11.9 kB]                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages            
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [1,801 B]                  
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages [3,006 B]           
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [3,790 B]            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en
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
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Fetched 20.8 kB in 2s (7,019 B/s)
W: Failed to fetch [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.

```

And here's what I got after doing sudo apt-get -f install:
```
elliot@ubuntu:~$ sudo apt-get -f install
sudo: /var/lib/sudo writable by non-owner (040770), should be mode 0700
[sudo] password for elliot: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  libqt4-webkit
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  mysql-server mysql-server-5.5
Suggested packages:
  tinyca
The following packages will be upgraded:
  mysql-server mysql-server-5.5
2 upgraded, 0 newly installed, 0 to remove and 355 not upgraded.
5 not fully installed or removed.
Need to get 8,838 kB of archives.
After this operation, 47.1 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main mysql-server all 5.5.34-0ubuntu0.12.04.1 [11.4 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main mysql-server-5.5 amd64 5.5.34-0ubuntu0.12.04.1 [8,827 kB]
Fetched 8,838 kB in 1min 1s (144 kB/s)                                         
Setting up linux-image-3.2.0-48-generic (3.2.0-48.74) ...
Running depmod.
Failed to run depmod
dpkg: error processing linux-image-3.2.0-48-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server-5.5:
 mysql-server-5.5 depends on mysql-server-core-5.5 (= 5.5.24-0ubuntu0.12.04.1); however:
  Version of mysql-server-core-5.5 on system is 5.5.34-0ubuntu0.12.04.1.
dpkg: error processing mysql-server-5.5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.5; however:
  Package mysql-server-5.5 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-48-generic; however:
  Package linux-image-3.2.0-48-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.48.58); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    No apport report written because MaxReports is reached already
                                  No apport report written because MaxReports is reached already
                Errors were encountered while processing:
 linux-image-3.2.0-48-generic
 mysql-server-5.5
 mysql-server
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

Thanks a lot for your help! I really need this fixed urgently because I can't install/update software, so any help would be appreciated!

-Elliot

---

### Post by xierdudeC on 2014-01-01
Hello,
The Ubuntu Software Center gives me "Packages cannot be installed or removed until the package system is repaired", but when I click "repair" it didn't work. I did sudo apt-get update and then sudo apt-get -f install but it didn't work.
When I try to install programs I get this:
```
The following packages have unmet dependencies:

mysql-server-5.5: PreDepends: mysql-common (>= 5.5.24-0ubuntu0.12.04.1) but 5.5.34-0ubuntu0.12.04.1 is installed
Depends: mysql-client-5.5 (>= 5.5.24-0ubuntu0.12.04.1) but 5.5.34-0ubuntu0.12.04.1 is installed
Depends: perl (>= 5.6) but 5.14.2-6ubuntu2.3 is installed
Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu4 is installed
Depends: upstart-job but it is a virtual package
Depends: mysql-server-core-5.5 (= 5.5.24-0ubuntu0.12.04.1) but 5.5.34-0ubuntu0.12.04.1 is installed



```Here's what I got after apt-get update:
```
elliot@ubuntu:~$ sudo apt-get updatesudo: /var/lib/sudo writable by non-owner (040770), should be mode 0700
[sudo] password for elliot: 
Hit [http://dl.google.com]("http://dl.google.com/") stable Release.gpg
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise Release.gpg 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates Release.gpg 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-backports Release.gpg 
Hit [http://dl.google.com]("http://dl.google.com/") stable Release 
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security Release.gpg 
Get:1 [http://ppa.launchpad.net]("http://ppa.launchpad.net/") precise Release.gpg [316 B] 
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") precise Release.gpg 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise Release 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates Release 
Hit [http://dl.google.com]("http://dl.google.com/") stable/main amd64 Packages 
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security Release 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-backports Release 
Hit [http://dl.google.com]("http://dl.google.com/") stable/main i386 Packages 
Ign [http://dl.google.com]("http://dl.google.com/") stable/main TranslationIndex 
Get:2 [http://ppa.launchpad.net]("http://ppa.launchpad.net/") precise Release [11.9 kB] 
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/restricted Sources 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/restricted Sources 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/main Sources 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/multiverse Sources 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/universe Sources 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/main amd64 Packages 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/restricted amd64 Packages 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/universe amd64 Packages 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/multiverse amd64 Packages 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/main i386 Packages 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/restricted i386 Packages 
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/main Sources 
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/multiverse Sources 
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/universe Sources 
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/main amd64 Packages 
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/restricted amd64 Packages 
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/universe amd64 Packages 
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/multiverse amd64 Packages 
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/main i386 Packages 
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/restricted i386 Packages 
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/universe i386 Packages 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/universe i386 Packages 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/multiverse i386 Packages 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/main TranslationIndex 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/multiverse TranslationIndex 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/restricted TranslationIndex 
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/multiverse i386 Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/main TranslationIndex 
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") precise Release 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/universe TranslationIndex 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/restricted Sources 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/main Sources 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/multiverse Sources 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/universe Sources 
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/multiverse TranslationIndex 
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/restricted TranslationIndex 
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/universe TranslationIndex 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/main amd64 Packages 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/restricted amd64 Packages 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/universe amd64 Packages 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/multiverse amd64 Packages 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/main i386 Packages 
Get:3 [http://ppa.launchpad.net]("http://ppa.launchpad.net/") precise/main Sources [1,801 B] 
Get:4 [http://ppa.launchpad.net]("http://ppa.launchpad.net/") precise/main amd64 Packages [3,006 B] 
Get:5 [http://ppa.launchpad.net]("http://ppa.launchpad.net/") precise/main i386 Packages [3,790 B] 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/restricted i386 Packages 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/universe i386 Packages 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/multiverse i386 Packages 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/main TranslationIndex 
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/main Translation-en 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/multiverse TranslationIndex 
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") precise/main TranslationIndex 
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") precise/main TranslationIndex 
Ign [http://dl.google.com]("http://dl.google.com/") stable/main Translation-en_US 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/restricted TranslationIndex 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/universe TranslationIndex
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-backports/main Sources 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-backports/restricted Sources 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-backports/universe Sources 
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/multiverse Translation-en 
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/restricted Translation-en 
Ign [http://dl.google.com]("http://dl.google.com/") stable/main Translation-en 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-backports/multiverse Sources 
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") precise-security/universe Translation-en
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-backports/main amd64 Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-backports/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-backports/universe amd64 Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-backports/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-backports/main TranslationIndex
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-backports/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-backports/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-backports/universe TranslationIndex
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/main Translation-en
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/multiverse Translation-en
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/restricted Translation-en
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise/universe Translation-en
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/main Translation-en
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-backports/main Translation-en
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") precise-backports/universe Translation-en
Err [http://ppa.launchpad.net]("http://ppa.launchpad.net/") precise/main Sources
404 Not Found
Err [http://ppa.launchpad.net]("http://ppa.launchpad.net/") precise/main amd64 Packages
404 Not Found
Err [http://ppa.launchpad.net]("http://ppa.launchpad.net/") precise/main i386 Packages
404 Not Found
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") precise/main Translation-en_US
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") precise/main Translation-en
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") precise/main Translation-en_US
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") precise/main Translation-en
Fetched 20.8 kB in 2s (7,019 B/s)
W: Failed to fetch [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/source/Sources) 404 Not Found


W: Failed to fetch [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/binary-amd64/Packages) 404 Not Found


W: Failed to fetch [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/binary-i386/Packages) 404 Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.

```

And here's what I got after doing sudo apt-get -f install:
```
elliot@ubuntu:~$ sudo apt-get -f install
sudo: /var/lib/sudo writable by non-owner (040770), should be mode 0700
[sudo] password for elliot: 
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
libqt4-webkit
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
mysql-server mysql-server-5.5
Suggested packages:
tinyca
The following packages will be upgraded:
mysql-server mysql-server-5.5
2 upgraded, 0 newly installed, 0 to remove and 355 not upgraded.
5 not fully installed or removed.
Need to get 8,838 kB of archives.
After this operation, 47.1 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main mysql-server all 5.5.34-0ubuntu0.12.04.1 [11.4 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main mysql-server-5.5 amd64 5.5.34-0ubuntu0.12.04.1 [8,827 kB]
Fetched 8,838 kB in 1min 1s (144 kB/s) 
Setting up linux-image-3.2.0-48-generic (3.2.0-48.74) ...
Running depmod.
Failed to run depmod
dpkg: error processing linux-image-3.2.0-48-generic (--configure):
subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server-5.5:
mysql-server-5.5 depends on mysql-server-core-5.5 (= 5.5.24-0ubuntu0.12.04.1); however:
Version of mysql-server-core-5.5 on system is 5.5.34-0ubuntu0.12.04.1.
dpkg: error processing mysql-server-5.5 (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mysql-server:
mysql-server depends on mysql-server-5.5; however:
Package mysql-server-5.5 is not configured yet.
dpkg: error processing mysql-server (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
linux-image-generic depends on linux-image-3.2.0-48-generic; however:
Package linux-image-3.2.0-48-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
linux-generic depends on linux-image-generic (= 3.2.0.48.58); however:
Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
Errors were encountered while processing:
linux-image-3.2.0-48-generic
mysql-server-5.5
mysql-server
linux-image-generic
linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

Thanks a lot for your help! I really need this fixed urgently because I can't install/update software, so any help would be appreciated!

-Elliot

---

### Post by QIII on 2014-01-01
Threads merged.

Please do not start duplicate threads in different parts of the forum.  It dilutes the community's effort and makes it less likely you will get help.

If you post in one area and realize later it would better have been in another, use the "Report Post" button and ask the staff to move the thread.

---

### Post by xierdudeC on 2014-01-01
Sorry, I didn't know.

---

### Post by ian-weisser on 2014-01-02
> **xierdudeC said:**
> 
mysql-server-5.5: PreDepends: mysql-common (>= 5.5.24-0ubuntu0.12.04.1) but 5.5.34-0ubuntu0.12.04.1 is installed
Depends: mysql-client-5.5 (>= 5.5.24-0ubuntu0.12.04.1) but 5.5.34-0ubuntu0.12.04.1 is installed
Depends: perl (>= 5.6) but 5.14.2-6ubuntu2.3 is installed
Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu4 is installed
Depends: upstart-job but it is a virtual package
Depends: mysql-server-core-5.5 (= 5.5.24-0ubuntu0.12.04.1) but 5.5.34-0ubuntu0.12.04.1 is installed



1) Disable all your PPAs and other non-Ubuntu software.
Your system is trying to tell you that you have added a PPA or other non-Ubuntu package that requires *older* versions than you currently have installed. Disabling the PPA will resolve the problem.

2) Update your package index to flush away the PPA dependencies: **sudo apt-get install update**

3) Upgrade your system normally: [B]sudo apt-get upgrade
[/B]You may have many upgrades awaiting you. Judging by your kernel version, you broke your package manager by adding that PPA many weeks ago.

---

### Post by jeanjd63 on 2014-01-02
Hello,

Can you give the return of this commande :
**dpkg -l  | grep -i  mysql**

---

### Post by oldos2er on 2014-01-02
This > sudo: /var/lib/sudo writable by non-owner (040770), should be mode 0700 is a big problem that needs to be fixed. ```
pkexec chmod 0755 /mnt/var/lib/sudo

pkexec chmod 0700 /mnt/var/lib/sudo/user
``` Replace "user" with your user name.

[Source]("http://askubuntu.com/questions/240252/sudo-var-lib-sudo-navneet-writable-by-non-owner-040777-should-be-mode-0700").

---

### Post by xierdudeC on 2014-01-02
This is what I got for **dpkg -l | grep -i mysql**:
```
ii  libdbd-mysql-perl                      4.020-1build2                           Perl5 database interface to the MySQL databaseii  libmysqlclient16                       5.1.62-0ubuntu0.11.10.1                 MySQL database client library
ii  libmysqlclient18                       5.5.32-0ubuntu0.12.04.1                 MySQL database client library
ii  libqt4-sql-mysql                       4:4.8.1-0ubuntu4.4                      Qt 4 MySQL database driver
ii  mysql-client-5.5                       5.5.34-0ubuntu0.12.04.1                 MySQL database client binaries
ii  mysql-client-core-5.5                  5.5.32-0ubuntu0.12.04.1                 MySQL database core client binaries
ii  mysql-common                           5.5.34-0ubuntu0.12.04.1                 MySQL database common files, e.g. /etc/mysql/my.cnf
iU  mysql-server                           5.5.32-0ubuntu0.12.04.1                 MySQL database server (metapackage depending on the latest version)
rc  mysql-server-5.1                       5.1.62-0ubuntu0.11.10.1                 MySQL database server binaries and system database setup
iU  mysql-server-5.5                       5.5.24-0ubuntu0.12.04.1                 MySQL database server binaries and system database setup
ii  mysql-server-core-5.5                  5.5.34-0ubuntu0.12.04.1                 MySQL database server binaries
ii  php5-mysql                             5.3.10-1ubuntu3.7                       MySQL module for php5



```

---

### Post by xierdudeC on 2014-01-02
I disabled PPAs and ran sudo apt-get update. I then ran sudo apt-get -f upgrade and it STILL DOESN'T WORK!!! HELP!!!
I got a big stream of stuff that upgrade was doing and then this:
```
Running depmod.Failed to run depmod
dpkg: error processing linux-image-3.2.0-48-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-48-generic; however:
  Package linux-image-3.2.0-48-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.48.58); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                          Setting up apparmor (2.7.102-0ubuntu3.9) ...
Installing new version of config file /etc/apparmor.d/abstractions/ubuntu-browsers.d/ubuntu-integration ...
 * Starting AppArmor profiles                                                   Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                         [ OK ]
 * Reloading AppArmor profiles                                                  Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                         [ OK ]
Processing triggers for libreoffice-common ...
Setting up libreoffice-emailmerge (1:3.5.7-0ubuntu5) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-48-generic
Warning: No support for locale: en_US.utf8
Errors were encountered while processing:
 mysql-server-5.5
 mysql-server
 grub-pc
 virtualbox-dkms
 linux-image-3.2.0-48-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by electrohandyman501 on 2014-01-02
Is this machine in a Virtbox as a guest? or is it a host? 
I see error entries for virtual box in with the other errors too.

---

### Post by deadflowr on 2014-01-02
3.2.0.48 is a really old kernel.
I don't what this would yield, but try
```
sudo apt-get update && sudo apt-get dist-upgrade
```
type it as is, and if anything comes up error-wise, post it.
Also, you can expand the scroll back of the terminal if needed by: 
Edit > Profile Preferences > Scrolling and mark Unlimited with a check.
This way you can scroll all the way back instead of only 500 lines, which happens.

---

### Post by xierdudeC on 2014-01-13
It's a wubi install.

---

### Post by jeanjd63 on 2014-01-15
You can try to download this file :
```
[B]wget  http://security.ubuntu.com/ubuntu/pool/main/m/mysql-5.5/mysql-server-5.5_5.5.34-0ubuntu0.12.04.1_amd64.deb
[/B]
```then execute this command :
[B]sudo  dpkg  -i  --force-all  mysql-server-5.5_5.5.34-0ubuntu0.12.04.1_amd64.deb
sudo  apt-get  install  -f[/B]

---

