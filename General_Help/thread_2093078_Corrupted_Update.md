---
title: "Corrupted Update"
date: 2012-12-09
forum: General Help
---

### Post by BronyVasNormandy on 2012-12-09
A little while ago, I tried to install some updates through the update manager. Unfortunately, due my fragile internet connection, the updates didn't install correctly or download completely. Now, whenever I try to update, I get this message:



"Previous installation hasn't been completed

The installation could have failed because of an error in the corresponding software package or it was cancelled in an unfriendly way. You have to repair this before you can install or remove any further software.


E:Method  has died unexpectedly!, E:Sub-process  returned an error code (100),
E:Method /usr/lib/apt/methods/ did not start correctly"



I assume I have to clear the previous installation attempt, but I can't figure out how.

Also, I have only been using Ubuntu for three months, and do not have much experience with it.

---

### Post by Kirk Schnable on 2012-12-09
A few quick commands you can try which might get your Apt up and running again quickly...

```
sudo apt-get -f install
```

```
sudo dpkg --configure -a
```

---

### Post by BronyVasNormandy on 2012-12-09
Okay, just tried running both of those and the update manager still returns the same message. Here's what the terminal showed.


blake@blake-OptiPlex-GX620:~$ sudo apt-get -f install
[sudo] password for blake: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic-pae
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 287 not upgraded.
blake@blake-OptiPlex-GX620:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic-pae
0 upgraded, 0 newly installed, 2 to remove and 287 not upgraded.
After this operation, 67.5 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 187001 files and directories currently installed.)
Removing linux-headers-3.2.0-29-generic-pae ...
Removing linux-headers-3.2.0-29 ...

---

### Post by Bucky Ball on 2012-12-09
That all looks fine. Now try:

```

sudo apt-get update
```... and:

```
sudo apt-get upgrade
```This will not upgrade your release to the next but only installed stuff that needs upgrading.

---

### Post by BronyVasNormandy on 2012-12-09
Tried the first one, and got this back from the terminal:

[SIZE="1"]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Get:3 [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg [198 B]                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Get:5 [http://archive.canonical.com](http://archive.canonical.com) precise Release [7,078 B]                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg [198 B]       
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Get:8 [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources [4,515 B]           
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [58.4 kB]       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]          
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                   
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources             
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources               
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources             
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages             
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages       
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages         
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages       
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en_US         
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en_US   
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en_US   
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en_US     
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
  Unable to connect to extras.ubuntu.com:http:
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
  Unable to connect to extras.ubuntu.com:http:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
  Unable to connect to ppa.launchpad.net:http:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
  Unable to connect to extras.ubuntu.com:http:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
  Unable to connect to ppa.launchpad.net:http:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
  Unable to connect to ppa.launchpad.net:http:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release                       
  
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                     
  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex
Err [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US
  Unable to connect to dl.google.com:http: [IP: 74.125.227.136 80]
Err [http://dl.google.com](http://dl.google.com) stable/main Translation-en
  Unable to connect to dl.google.com:http: [IP: 74.125.227.136 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Fetched 62.0 kB in 4s (12.7 kB/s)
Reading package lists... Done
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release)  

W: Failed to fetch [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/precise/main/binary-i386/Packages)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en_US](http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en_US)  Unable to connect to dl.google.com:http: [IP: 74.125.227.136 80]

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en](http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en)  Unable to connect to dl.google.com:http: [IP: 74.125.227.136 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en_US](http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en_US)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en_US](http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en_US)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en_US](http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en_US)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en_US](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en_US)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_US](http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_US)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en](http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/precise/main/i18n/Translation-en_US](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/precise/main/i18n/Translation-en_US)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/precise/main/i18n/Translation-en](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/precise/main/i18n/Translation-en)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_US)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en_US)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en_US)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en_US)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en_US)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en_US)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en_US)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en_US)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en_US)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en_US)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en_US)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en_US)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Some index files failed to download. They have been ignored, or old ones used instead.[/SIZE]



After trying the second one I got this back from the terminal:

[SIZE="1"]blake@blake-OptiPlex-GX620:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  ginn libgrip0 libunity-2d-private0 libunity-core-5.0-5 linux-generic-pae
  linux-headers-generic-pae linux-image-generic-pae unity unity-2d-common
  unity-2d-panel unity-2d-shell unity-2d-spread unity-common unity-services
The following packages will be upgraded:
  accountsservice activity-log-manager-common
  activity-log-manager-control-center apparmor appmenu-gtk appmenu-gtk3 apport
  apport-gtk apport-symptoms apt apt-transport-https apt-utils aptdaemon
  aptdaemon-data bamfdaemon base-files bind9-host brasero brasero-cdrkit
  brasero-common busybox-initramfs busybox-static colord compiz compiz-core
  compiz-gnome compiz-plugins compiz-plugins-default coreutils cups cups-bsd
  cups-client cups-common cups-ppdc dbus dbus-x11 dnsutils eog evince
  evince-common firefox firefox-globalmenu firefox-gnome-support
  firefox-locale-en flashplugin-installer fonts-liberation ghostscript
  ghostscript-cups ghostscript-x gimp gimp-data gir1.2-accountsservice-1.0
  gir1.2-gtk-3.0 gir1.2-gudev-1.0 gir1.2-javascriptcoregtk-3.0 gir1.2-rb-3.0
  gir1.2-totem-1.0 gir1.2-webkit-3.0 gnome-accessibility-themes
  gnome-control-center gnome-control-center-data gnome-icon-theme gnome-media
  gnome-orca gnome-power-manager gnome-settings-daemon gnome-themes-standard
  gnupg google-chrome-stable gpgv grub-common grub-pc grub-pc-bin grub2-common
  gstreamer0.10-plugins-bad gvfs gvfs-backends gvfs-bin gvfs-common
  gvfs-daemons gvfs-fuse gvfs-libs im-switch indicator-messages
  indicator-status-provider-mc5 indicator-status-provider-pidgin
  isc-dhcp-client isc-dhcp-common jockey-common jockey-gtk
  landscape-client-ui-install language-pack-en language-pack-en-base
  language-pack-gnome-en language-pack-gnome-en-base libaccountsservice0
  libapt-inst1.4 libapt-pkg4.12 libart-2.0-2 libavcodec53 libavformat53
  libavutil51 libbamf0 libbamf3-0 libbind9-80 libbrasero-media3-1 libc-bin
  libc-dev-bin libc6 libc6-dev libcolord1 libcups2 libcupscgi1 libcupsdriver1
  libcupsimage2 libcupsmime1 libcupsppdc1 libdbus-1-3 libdecoration0 libdns81
  libevince3-3 libfreerdp-plugins-standard libfreerdp1 libgail-3-0 libgimp2.0
  libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libglu1-mesa
  libgnome-control-center1 libgnome2-common libgs9 libgs9-common
  libgstreamer-plugins-bad0.10-0 libgtk-3-0 libgtk-3-bin libgtk-3-common
  libgudev-1.0-0 libindicator-messages-status-provider1 libisc83 libisccc80
  libisccfg82 libjavascriptcoregtk-1.0-0 libjavascriptcoregtk-3.0-0
  libjs-jquery libldap-2.4-2 liblwres80 libnautilus-extension1a libnux-2.0-0
  libnux-2.0-common libparted0debian1 libperl5.14 libpostproc52 libproxy1
  libproxy1-plugin-gsettings libproxy1-plugin-networkmanager libqt4-dbus
  libqt4-declarative libqt4-network libqt4-opengl libqt4-script libqt4-sql
  libqt4-sql-sqlite libqt4-svg libqt4-xml libqt4-xmlpatterns libqtcore4
  libqtgui4 librhythmbox-core5 libssh-4 libswscale2 libtiff4 libtotem0
  libudev0 libwebkitgtk-1.0-0 libwebkitgtk-1.0-common libwebkitgtk-3.0-0
  libwebkitgtk-3.0-common libxatracker1 libxcb-composite0 libxcb-dri2-0
  libxcb-glx0 libxcb-randr0 libxcb-render0 libxcb-shape0 libxcb-shm0
  libxcb-xv0 libxcb1 libxml2 libxslt1.1 light-themes linux-firmware
  linux-libc-dev login lsb-base lsb-release make multiarch-support nautilus
  nautilus-data ntfs-3g nux-tools nvidia-common onboard oneconf parted passwd
  perl perl-base perl-modules python-apport python-aptdaemon
  python-aptdaemon.gtk3widgets python-aptdaemon.pkcompat python-central
  python-keyring python-libproxy python-libxml2 python-problem-report
  python-software-properties python-ubuntu-sso-client qdbus resolvconf
  rhythmbox rhythmbox-data rhythmbox-mozilla rhythmbox-plugin-cdrecorder
  rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins
  seahorse sessioninstaller software-center software-properties-common
  software-properties-gtk ssl-cert thunderbird thunderbird-globalmenu
  thunderbird-gnome-support thunderbird-locale-en thunderbird-locale-en-us
  totem totem-common totem-mozilla totem-plugins transmission-common
  transmission-gtk tzdata ubuntu-docs ubuntu-keyring ubuntu-sso-client
  ubuntu-sso-client-gtk ubuntuone-control-panel ubuntuone-installer udev
  unity-2d unity-greeter unity-lens-video unity-scope-video-remote
  update-manager update-manager-core update-notifier update-notifier-common
  wpasupplicant x11-utils xdiagnose xserver-common xserver-xorg-core
  xserver-xorg-input-synaptics xserver-xorg-input-wacom
  xserver-xorg-video-intel xterm xul-ext-ubufox
273 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
Failed to exec method /usr/lib/apt/methods/
E: Method  has died unexpectedly!
E: Sub-process  returned an error code (100)
E: Method /usr/lib/apt/methods/ did not start correctly[/SIZE]

Apologies for stretching the page.

---

### Post by ibjsb4 on 2012-12-09
First off

Please edit that long post and use code tags.

```
[SIZE=1]Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Get:3 [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg [198 B]                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Get:5 [http://archive.canonical.com](http://archive.canonical.com) precise Release [7,078 B]                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg [198 B]       
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Get:8 [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources [4,515 B]           
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [58.4 kB]       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]          
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                   
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources             
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources               
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources             
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages             
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages       
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages         
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages       
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en_US         
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en_US   
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en_US   
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en_US     
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
  Unable to connect to extras.ubuntu.com:http:
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
  Unable to connect to extras.ubuntu.com:http:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
  Unable to connect to ppa.launchpad.net:http:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
  Unable to connect to extras.ubuntu.com:http:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
  Unable to connect to ppa.launchpad.net:http:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
  Unable to connect to ppa.launchpad.net:http:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release                       
  
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                     
  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex
Err [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US
  Unable to connect to dl.google.com:http: [IP: 74.125.227.136 80]
Err [http://dl.google.com](http://dl.google.com) stable/main Translation-en
  Unable to connect to dl.google.com:http: [IP: 74.125.227.136 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Fetched 62.0 kB in 4s (12.7 kB/s)
Reading package lists... Done
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dist...-i386/Packages]("http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages")  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...pdates/Release]("http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release")  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...kports/Release]("http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release")  

W: Failed to fetch [http://ppa.launchpad.net/nilarimogar...-i386/Packages]("http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/precise/main/binary-i386/Packages")  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...source/Sources]("http://security.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources")  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...source/Sources]("http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources")  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...source/Sources]("http://security.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources")  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...source/Sources]("http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources")  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...-i386/Packages]("http://security.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages")  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...-i386/Packages]("http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages")  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...-i386/Packages]("http://security.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages")  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...-i386/Packages]("http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages")  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch [http://dl.google.com/linux/chrome/de...nslation-en_US]("http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en_US")  Unable to connect to dl.google.com:http: [IP: 74.125.227.136 80]

W: Failed to fetch [http://dl.google.com/linux/chrome/de...Translation-en]("http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en")  Unable to connect to dl.google.com:http: [IP: 74.125.227.136 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...nslation-en_US]("http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en_US")  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...Translation-en]("http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en")  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...nslation-en_US]("http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en_US")  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...Translation-en]("http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en")  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...nslation-en_US]("http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en_US")  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...Translation-en]("http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en")  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...nslation-en_US]("http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en_US")  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...Translation-en]("http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en")  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.184 80]

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dist...nslation-en_US]("http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_US")  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dist...Translation-en]("http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en")  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://ppa.launchpad.net/nilarimogar...nslation-en_US]("http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/precise/main/i18n/Translation-en_US")  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://ppa.launchpad.net/nilarimogar...Translation-en]("http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/precise/main/i18n/Translation-en")  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...source/Sources]("http://us.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...source/Sources]("http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...source/Sources]("http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...source/Sources]("http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...-i386/Packages]("http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...-i386/Packages]("http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...-i386/Packages]("http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...-i386/Packages]("http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...nslation-en_US]("http://us.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_US")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...Translation-en]("http://us.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...nslation-en_US]("http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en_US")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...Translation-en]("http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...nslation-en_US]("http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en_US")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...Translation-en]("http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...nslation-en_US]("http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en_US")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...Translation-en]("http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...source/Sources]("http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...source/Sources]("http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...source/Sources]("http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...source/Sources]("http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...-i386/Packages]("http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...-i386/Packages]("http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...-i386/Packages]("http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...-i386/Packages]("http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...nslation-en_US]("http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en_US")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...Translation-en]("http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...nslation-en_US]("http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en_US")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...Translation-en]("http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...nslation-en_US]("http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en_US")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...Translation-en]("http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...nslation-en_US]("http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en_US")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...Translation-en]("http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...source/Sources]("http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...source/Sources]("http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...source/Sources]("http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...source/Sources]("http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...-i386/Packages]("http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...-i386/Packages]("http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...-i386/Packages]("http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...-i386/Packages]("http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...nslation-en_US]("http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en_US")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...Translation-en]("http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...nslation-en_US]("http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en_US")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...Translation-en]("http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...nslation-en_US]("http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en_US")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...Translation-en]("http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...nslation-en_US]("http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en_US")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...Translation-en]("http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en")  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Some index files failed to download. They have been ignored, or old ones used instead.[/SIZE]



After trying the second one I got this back from the terminal:

[SIZE=1]blake@blake-OptiPlex-GX620:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  ginn libgrip0 libunity-2d-private0 libunity-core-5.0-5 linux-generic-pae
  linux-headers-generic-pae linux-image-generic-pae unity unity-2d-common
  unity-2d-panel unity-2d-shell unity-2d-spread unity-common unity-services
The following packages will be upgraded:
  accountsservice activity-log-manager-common
  activity-log-manager-control-center apparmor appmenu-gtk appmenu-gtk3 apport
  apport-gtk apport-symptoms apt apt-transport-https apt-utils aptdaemon
  aptdaemon-data bamfdaemon base-files bind9-host brasero brasero-cdrkit
  brasero-common busybox-initramfs busybox-static colord compiz compiz-core
  compiz-gnome compiz-plugins compiz-plugins-default coreutils cups cups-bsd
  cups-client cups-common cups-ppdc dbus dbus-x11 dnsutils eog evince
  evince-common firefox firefox-globalmenu firefox-gnome-support
  firefox-locale-en flashplugin-installer fonts-liberation ghostscript
  ghostscript-cups ghostscript-x gimp gimp-data gir1.2-accountsservice-1.0
  gir1.2-gtk-3.0 gir1.2-gudev-1.0 gir1.2-javascriptcoregtk-3.0 gir1.2-rb-3.0
  gir1.2-totem-1.0 gir1.2-webkit-3.0 gnome-accessibility-themes
  gnome-control-center gnome-control-center-data gnome-icon-theme gnome-media
  gnome-orca gnome-power-manager gnome-settings-daemon gnome-themes-standard
  gnupg google-chrome-stable gpgv grub-common grub-pc grub-pc-bin grub2-common
  gstreamer0.10-plugins-bad gvfs gvfs-backends gvfs-bin gvfs-common
  gvfs-daemons gvfs-fuse gvfs-libs im-switch indicator-messages
  indicator-status-provider-mc5 indicator-status-provider-pidgin
  isc-dhcp-client isc-dhcp-common jockey-common jockey-gtk
  landscape-client-ui-install language-pack-en language-pack-en-base
  language-pack-gnome-en language-pack-gnome-en-base libaccountsservice0
  libapt-inst1.4 libapt-pkg4.12 libart-2.0-2 libavcodec53 libavformat53
  libavutil51 libbamf0 libbamf3-0 libbind9-80 libbrasero-media3-1 libc-bin
  libc-dev-bin libc6 libc6-dev libcolord1 libcups2 libcupscgi1 libcupsdriver1
  libcupsimage2 libcupsmime1 libcupsppdc1 libdbus-1-3 libdecoration0 libdns81
  libevince3-3 libfreerdp-plugins-standard libfreerdp1 libgail-3-0 libgimp2.0
  libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libglu1-mesa
  libgnome-control-center1 libgnome2-common libgs9 libgs9-common
  libgstreamer-plugins-bad0.10-0 libgtk-3-0 libgtk-3-bin libgtk-3-common
  libgudev-1.0-0 libindicator-messages-status-provider1 libisc83 libisccc80
  libisccfg82 libjavascriptcoregtk-1.0-0 libjavascriptcoregtk-3.0-0
  libjs-jquery libldap-2.4-2 liblwres80 libnautilus-extension1a libnux-2.0-0
  libnux-2.0-common libparted0debian1 libperl5.14 libpostproc52 libproxy1
  libproxy1-plugin-gsettings libproxy1-plugin-networkmanager libqt4-dbus
  libqt4-declarative libqt4-network libqt4-opengl libqt4-script libqt4-sql
  libqt4-sql-sqlite libqt4-svg libqt4-xml libqt4-xmlpatterns libqtcore4
  libqtgui4 librhythmbox-core5 libssh-4 libswscale2 libtiff4 libtotem0
  libudev0 libwebkitgtk-1.0-0 libwebkitgtk-1.0-common libwebkitgtk-3.0-0
  libwebkitgtk-3.0-common libxatracker1 libxcb-composite0 libxcb-dri2-0
  libxcb-glx0 libxcb-randr0 libxcb-render0 libxcb-shape0 libxcb-shm0
  libxcb-xv0 libxcb1 libxml2 libxslt1.1 light-themes linux-firmware
  linux-libc-dev login lsb-base lsb-release make multiarch-support nautilus
  nautilus-data ntfs-3g nux-tools nvidia-common onboard oneconf parted passwd
  perl perl-base perl-modules python-apport python-aptdaemon
  python-aptdaemon.gtk3widgets python-aptdaemon.pkcompat python-central
  python-keyring python-libproxy python-libxml2 python-problem-report
  python-software-properties python-ubuntu-sso-client qdbus resolvconf
  rhythmbox rhythmbox-data rhythmbox-mozilla rhythmbox-plugin-cdrecorder
  rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins
  seahorse sessioninstaller software-center software-properties-common
  software-properties-gtk ssl-cert thunderbird thunderbird-globalmenu
  thunderbird-gnome-support thunderbird-locale-en thunderbird-locale-en-us
  totem totem-common totem-mozilla totem-plugins transmission-common
  transmission-gtk tzdata ubuntu-docs ubuntu-keyring ubuntu-sso-client
  ubuntu-sso-client-gtk ubuntuone-control-panel ubuntuone-installer udev
  unity-2d unity-greeter unity-lens-video unity-scope-video-remote
  update-manager update-manager-core update-notifier update-notifier-common
  wpasupplicant x11-utils xdiagnose xserver-common xserver-xorg-core
  xserver-xorg-input-synaptics xserver-xorg-input-wacom
  xserver-xorg-video-intel xterm xul-ext-ubufox
273 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
Failed to exec method /usr/lib/apt/methods/
E: Method  has died unexpectedly!
E: Sub-process  returned an error code (100)
E: Method /usr/lib/apt/methods/ did not start correctly[/SIZE]
```Check out post #9 on how to do that.

[http://ubuntuforums.org/showthread.php?t=2092468](http://ubuntuforums.org/showthread.php?t=2092468)

Im curious about what third party PPA's you have.  This could be a problem.

Would you open at terminal and enter:

```
grep ^ /etc/apt/sources.list.d/*
```

And please post the output.

---

### Post by Bucky Ball on 2012-12-09
Yep, looks like you have some problematic repos there. Have you upgraded from 12.04 to 12.10 lately by any chance?

---

