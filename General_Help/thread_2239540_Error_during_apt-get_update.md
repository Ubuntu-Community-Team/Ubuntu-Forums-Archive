---
title: "Error during apt-get update"
date: 2014-08-14
forum: General Help
---

### Post by ac98521 on 2014-08-14
Here's the last message I got. What is this please?

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 90BD7EACED8E640A

---

### Post by deadflowr on 2014-08-14
Perhaps the whole output of apt-get update will make more sense to us.
It will help determine exactly which ppa is busted.
ppa.launchpad.net is pretty generic in and of it's self.

---

### Post by ac98521 on 2014-08-14
Here you go.

```
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [59.7 kB]             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [38.7 kB]        
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [14 B]     
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [11.3 kB]    
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [699 B]    
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty InRelease                              
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [123 kB]   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_PH                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty-updates InRelease                      
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_PH                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty-backports InRelease                    
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg [316 B]                      
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty Release.gpg                            
Get:9 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty-updates Release.gpg [933 B]          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Get:10 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty-backports Release.gpg [933 B]       
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [14 B]
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty Release                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages/DiffIndex               
Get:12 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty-updates Release [59.7 kB]           
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [45.4 kB]
Get:14 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty-backports Release [59.7 kB]         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty/main Sources                           
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty/restricted Sources                     
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [1,398 B]
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty/main Translation-en                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_PH                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty/universe Translation-en                
Get:16 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty-updates/main Sources [107 kB]       
Get:17 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty-updates/restricted Sources [1,408 B]
Get:18 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty-updates/universe Sources [74.9 kB]  
Get:19 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty-updates/multiverse Sources [3,230 B]
Get:20 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty-updates/main i386 Packages [287 kB] 
Get:21 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty-updates/restricted i386 Packages [5,820 B]
Get:22 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty-updates/universe i386 Packages [181 kB]
Get:23 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [8,444 B]
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty-updates/universe Translation-en        
Get:24 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty-backports/main Sources [3,524 B]    
Get:25 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty-backports/restricted Sources [14 B] 
Get:26 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty-backports/universe Sources [11.0 kB]
Get:27 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty-backports/multiverse Sources [768 B]
Get:28 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty-backports/main i386 Packages [5,198 B]
Get:29 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty-backports/restricted i386 Packages [14 B]
Get:30 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty-backports/universe i386 Packages [14.5 kB]
Get:31 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty-backports/multiverse i386 Packages [619 B]
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty-backports/universe Translation-en      
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty/main Translation-en_PH                 
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty/multiverse Translation-en_PH
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty/restricted Translation-en_PH
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) trusty/universe Translation-en_PH
Fetched 1,108 kB in 34s (32.3 kB/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 90BD7EACED8E640A

```

---

### Post by oldos2er on 2014-08-14
There are a few different ways to add a missing key, mentioned here: [http://askubuntu.com/questions/13065/how-do-i-fix-the-gpg-error-no-pubkey](http://askubuntu.com/questions/13065/how-do-i-fix-the-gpg-error-no-pubkey)

---

### Post by ac98521 on 2014-08-16
thanks this problem is now solver

---

### Post by drizad on 2015-07-09
thanks... the link works for me..

---

