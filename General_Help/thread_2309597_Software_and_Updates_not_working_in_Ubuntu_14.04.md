---
title: "Software and Updates not working in Ubuntu 14.04"
date: 2016-01-11
forum: General Help
---

### Post by AbdRahim on 2016-01-11
Software and Updates not working in Ubuntu 14.04, Gnome 3. Cannot access repositories in Synaptic either.

Sudo apt-get update yeilds:
 
Reading state information... Done
W: Ignoring Provides line with DepCompareOp for package python-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package python-cffi-backend-api-min
W: Ignoring Provides line with DepCompareOp for package python3-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package python3-cffi-backend-api-min
W: Ignoring Provides line with DepCompareOp for package python-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package python-cffi-backend-api-min
W: Ignoring Provides line with DepCompareOp for package python3-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package python3-cffi-backend-api-min
W: You may want to run apt-get update to correct these problems

Tired purge, clea autoclean, uninstalled the updaters and reinstalled. Nothing seems to have an effect.

---

### Post by ian-weisser on 2016-01-12
Please show us the entire output of apt update.

---

### Post by AbdRahim on 2016-01-13
```
abc@xxxx:~$ sudo apt-get update
[sudo] password for xxxx: 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease
Hit [http://download.virtualbox.org](http://download.virtualbox.org) trusty InRelease                            
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease [64.4 kB]           
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease [64.4 kB]          
Hit [http://download.virtualbox.org](http://download.virtualbox.org) trusty/contrib amd64 Packages               
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Ign [http://linux.dropbox.com](http://linux.dropbox.com) trusty InRelease                                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease [16.0 kB]                      
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease [64.5 kB]        
Hit [http://download.virtualbox.org](http://download.virtualbox.org) trusty/contrib i386 Packages                
Ign [http://ubuntu-cloud.archive.canonical.com](http://ubuntu-cloud.archive.canonical.com) trusty-updates/liberty InRelease 
Hit [http://linux.dropbox.com](http://linux.dropbox.com) trusty Release.gpg                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [248 kB]        
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [103 kB]         
Ign [http://download.bitdefender.com](http://download.bitdefender.com) bitdefender InRelease                      
Get:7 [http://deb.opera.com](http://deb.opera.com) stable InRelease [2,590 B]                          
Get:8 [http://ubuntu-cloud.archive.canonical.com](http://ubuntu-cloud.archive.canonical.com) trusty-updates/liberty Release.gpg [543 B]
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://download.bitdefender.com](http://download.bitdefender.com) bitdefender Release.gpg                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://download.bitdefender.com](http://download.bitdefender.com) bitdefender Release                        
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [5,359 B] 
Hit [http://linux.dropbox.com](http://linux.dropbox.com) trusty Release                                    
Hit [http://download.bitdefender.com](http://download.bitdefender.com) bitdefender/non-free amd64 Packages        
Get:10 [http://ubuntu-cloud.archive.canonical.com](http://ubuntu-cloud.archive.canonical.com) trusty-updates/liberty Release [6,723 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [146 kB]   
Get:12 [http://deb.opera.com](http://deb.opera.com) stable/non-free amd64 Packages [1,814 B]           
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages                 
Hit [http://download.bitdefender.com](http://download.bitdefender.com) bitdefender/non-free i386 Packages         
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [4,035 B] 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [5,161 B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [32.7 kB]   
Get:16 [http://ubuntu-cloud.archive.canonical.com](http://ubuntu-cloud.archive.canonical.com) trusty-updates/liberty/main amd64 Packages [147 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main amd64 Packages [683 kB]
Ign [http://download.virtualbox.org](http://download.virtualbox.org) trusty/contrib Translation-en_US            
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [2,357 B] 
Hit [http://linux.dropbox.com](http://linux.dropbox.com) trusty/main amd64 Packages                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Get:19 [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages [1,649 B]            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://download.virtualbox.org](http://download.virtualbox.org) trusty/contrib Translation-en               
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages [404 kB] 
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [15.9 kB]
Get:22 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages [72.6 kB]           
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe amd64 Packages [333 kB]
Hit [http://linux.dropbox.com](http://linux.dropbox.com) trusty/main i386 Packages                         
Hit [http://deb.torproject.org](http://deb.torproject.org) trusty InRelease                                 
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [13.0 kB]
Hit [http://deb.torproject.org](http://deb.torproject.org) trusty/main amd64 Packages                       
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [659 kB] 
Hit [http://deb.torproject.org](http://deb.torproject.org) trusty/main i386 Packages                        
Get:26 [http://ubuntu-cloud.archive.canonical.com](http://ubuntu-cloud.archive.canonical.com) trusty-updates/liberty/main i386 Packages [147 kB]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [15.6 kB]
Get:28 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages [72.6 kB]            
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [334 kB]
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages [13.0 kB]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [13.1 kB]
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages [123 kB]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en [343 kB]
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en [6,832 B]
Ign [http://deb.torproject.org](http://deb.torproject.org) trusty/main Translation-en_US                    
Get:35 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages [4,798 B]
Ign [http://deb.torproject.org](http://deb.torproject.org) trusty/main Translation-en                       
Get:36 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [379 kB]  
Get:37 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en [45.4 kB]           
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en [3,699 B]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en [175 kB]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources [8,221 B]    
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources [28 B] 
Ign [http://linux.dropbox.com](http://linux.dropbox.com) trusty/main Translation-en_US                     
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources [33.1 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US                     
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources [1,898 B]
Ign [http://linux.dropbox.com](http://linux.dropbox.com) trusty/main Translation-en                        
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main amd64 Packages [9,402 B]
Get:45 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [12.7 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted amd64 Packages [28 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Get:47 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [123 kB]
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en                        
Get:48 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe amd64 Packages [39.7 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Get:49 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages [1,571 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Get:50 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages [9,411 B]
Get:51 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [4,955 B]
Get:52 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages [28 B]
Get:53 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en [221 kB] 
Get:54 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages [39.7 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Get:55 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages [1,552 B]
Get:56 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en [5,549 B]
Get:57 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en [1,215 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Get:58 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en [2,437 B]
Get:59 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en [14 B]
Ign [http://ubuntu-cloud.archive.canonical.com](http://ubuntu-cloud.archive.canonical.com) trusty-updates/liberty/main Translation-en_US
Get:60 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en [3,206 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Get:61 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en [71.9 kB]
Get:62 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en [34.6 kB]
Ign [http://ubuntu-cloud.archive.canonical.com](http://ubuntu-cloud.archive.canonical.com) trusty-updates/liberty/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main amd64 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted amd64 Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe amd64 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse amd64 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en              
Ign [http://download.bitdefender.com](http://download.bitdefender.com) bitdefender/non-free Translation-en_US     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [http://download.bitdefender.com](http://download.bitdefender.com) bitdefender/non-free Translation-en        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US
Fetched 5,397 kB in 5s (997 kB/s)            
Reading package lists... Done
W: Ignoring Provides line with DepCompareOp for package python-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package python-cffi-backend-api-min
W: Ignoring Provides line with DepCompareOp for package python3-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package python3-cffi-backend-api-min
W: Ignoring Provides line with DepCompareOp for package python-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package python-cffi-backend-api-min
W: Ignoring Provides line with DepCompareOp for package python3-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package python3-cffi-backend-api-min
W: You may want to run apt-get update to correct these problems
abc@xxx:~$
```

---

### Post by ian-weisser on 2016-01-13
Next, please show us the complete output of:
```
apt-cache policy python-cffi
```

---

