---
title: "The package system is broken,   cinnamon-control-center-data problem"
date: 2015-10-09
forum: General Help
---

### Post by SUPERFITTER on 2015-10-09
```
dennis@Dennis1:~$ sudo apt-get update
[sudo] password for dennis: 
Ign http://us.archive.ubuntu.com trusty InRelease
Hit http://us.archive.ubuntu.com trusty-updates InRelease                      
Hit http://us.archive.ubuntu.com trusty-backports InRelease                    
Hit http://archive.canonical.com quantal InRelease                             
Hit http://security.ubuntu.com trusty-security InRelease                       
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://ppa.launchpad.net trusty InRelease                                  
Get:1 http://us.archive.ubuntu.com trusty-updates/main Sources [238 kB]        
Hit http://archive.canonical.com trusty InRelease                              
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://security.ubuntu.com trusty-security/main Sources                    
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://archive.canonical.com quantal/partner Sources                       
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://security.ubuntu.com trusty-security/restricted Sources              
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:2 http://us.archive.ubuntu.com trusty-updates/restricted Sources [4,722 B] 
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Get:3 http://us.archive.ubuntu.com trusty-updates/universe Sources [140 kB]    
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://security.ubuntu.com trusty-security/universe Sources                
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Get:4 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [5,144 B] 
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Get:5 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [629 kB] 
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Get:6 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.4 kB]
Get:7 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [323 kB]
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages       
Get:8 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [11.9 kB]
Get:9 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [609 kB]  
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Ign http://archive.canonical.com trusty/partner Translation-en                 
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Get:10 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.1 kB]
Get:11 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [324 kB]
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Get:12 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [12.1 kB]
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en        
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/main Sources           
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en
Hit http://us.archive.ubuntu.com trusty Release   
Hit http://us.archive.ubuntu.com trusty/main Sources
Hit http://us.archive.ubuntu.com trusty/restricted Sources
Hit http://us.archive.ubuntu.com trusty/universe Sources
Hit http://us.archive.ubuntu.com trusty/multiverse Sources
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty/main i386 Packages
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty/main Translation-en
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty/universe Translation-en
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Fetched 2,328 kB in 4s (552 kB/s)
Reading package lists... Done
dennis@Dennis1:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 cinnamon-control-center : Depends: **cinnamon-control-center-data (= 2.6.0-20151008013046-trusty**) but 2.6.0-20151007013043-trusty is installed
E: Unmet dependencies. Try using -f.
dennis@Dennis1:~$  sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 cinnamon-control-center : Depends: cinnamon-control-center-data (= 2.6.0-20151008013046-trusty) but 2.6.0-20151007013043-trusty is installed
E: Unmet dependencies. Try using -f.
dennis@Dennis1:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
dennis@Dennis1:~$ 
```


Where do I get this version of Cinnamon: 
 cinnamon-control-center-data 2.6.0-20151008013046-trusty

This seems to be the problem?

---

### Post by ian-weisser on 2015-10-10
You get that version of cinnamon-control-center-data from the PPA you installed to get Cinnamon originally.
You should contact the PPA maintainers to let them know that their PPA has introduced a version conflict.

The Software Updater warning "The package system is broken" is caused by the version conflict. 
The apt-get -f flag is not a magic wand - it fixes many known kinds of problems, but it generally cannot fix version conflicts..

---

### Post by SUPERFITTER on 2015-10-10
Thank you ian-weisser for your response.


To  fix the problem, I went to Ubuntu Software Center.  A window opened  (see Attachment) and I clicked repair and waited for it to repair the  program.  You will see a progress Icon in the upper left of the Ubuntu Software Center.  Now reboot and I was able to get my updates for Ubuntu.

---

