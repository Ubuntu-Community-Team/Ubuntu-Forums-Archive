---
title: "E: Unable to locate package"
date: 2015-02-04
forum: General Help
---

### Post by akalovid on 2015-02-04
Dear friends,

I am desperate. I am running
[INDENT]DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"

[/INDENT]
A while ago I noticed I am unable to install anything, be it through synaptic or apt-get. I was getting errors like here:

[http://askubuntu.com/questions/146362/getting-error-on-downloading-updates](http://askubuntu.com/questions/146362/getting-error-on-downloading-updates)

(Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main gnome-control-center-data all 1:3.4.2-0ubuntu0.2
  Connection failed [IP: 91.189.92.183 80])

I followed the advice on the site above and it didn't work. I tried to revert the changes copying the commands on the site and ended up worse than before.
Now I only get this error
[INDENT]ludi@ubuntu:~$ sudo apt-get install pdfshuffler 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package pdfshuffler
[/INDENT]
or this error depending on package
[INDENT]ludi@ubuntu:~$ sudo apt-get install meld
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package meld is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
[/INDENT]
E: Package 'meld' has no installation candidate

I have tried with many packages and many download servers from the software sources tab. If I run update it goes like this:[INDENT]```
ludi@ubuntu:~$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release.gpg                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release                              
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Sources                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                     
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner amd64 Packages               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main amd64 Packages                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release.gpg                          
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner i386 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release.gpg                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release.gpg                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security Release.gpg                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                       
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en_US                   
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Sources   
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Sources
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Sources
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Sources
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Sources
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Sources
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Sources
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Sources
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Sources
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Sources
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Sources
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Sources
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/main Sources
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/restricted Sources
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/universe Sources
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/multiverse Sources
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/main amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/universe amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/main i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/restricted i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/universe i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.14 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/universe Translation-en
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/main/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/universe/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
```
[/INDENT]

I am desperately hoping for your help.

Akalovid

---

### Post by lisati on 2015-02-04
12.10 reached its end of life in May 2014. Please see this thread: [http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

---

