---
title: "Update Issues"
date: 2012-11-18
forum: General Help
---

### Post by Hiuhu on 2012-11-18
I have just installed ubuntu 12.04 I have a big problem updating it.
I tried the command sudo apt-get update & this is what I get :
jemoh@Lenovo-G580:~$ sudo apt-get update 
[sudo] password for jemoh: 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Get:1 [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg [198 B]                 
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Get:2 [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg [198 B]                 
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Get:3 [http://archive.canonical.com](http://archive.canonical.com) precise Release [7,078 B]                   
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Get:4 [http://archive.canonical.com](http://archive.canonical.com) precise Release [7,078 B]                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Get:5 [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages [7,410 B]    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Get:6 [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages [5,944 B]     
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Get:7 [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages [7,410 B]    
Get:8 [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages [5,944 B]     
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise InRelease                            
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free amd64 Packages                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free amd64 Packages              
Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                    
Ign [http://mirror01.th.ifl.net](http://mirror01.th.ifl.net) precise InRelease                               
Ign [http://mirror01.th.ifl.net](http://mirror01.th.ifl.net) precise-updates InRelease                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages                   
Ign [http://mirror01.th.ifl.net](http://mirror01.th.ifl.net) precise-security InRelease                      
Ign [http://mirror01.th.ifl.net](http://mirror01.th.ifl.net) precise-backports InRelease                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free i386 Packages               
Get:11 [http://mirror01.th.ifl.net](http://mirror01.th.ifl.net) precise Release.gpg [198 B]                  
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Err [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
  Error reading from server - read (104: Connection reset by peer) [IP: 173.194.34.132 80]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free TranslationIndex                
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Err [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
  Error reading from server - read (104: Connection reset by peer) [IP: 173.194.34.132 80]
Get:12 [http://mirror01.th.ifl.net](http://mirror01.th.ifl.net) precise-updates Release.gpg [198 B]          
Get:13 [http://mirror01.th.ifl.net](http://mirror01.th.ifl.net) precise-updates Release.gpg [198 B]          
Get:14 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                    
Get:15 [http://mirror01.th.ifl.net](http://mirror01.th.ifl.net) precise-updates Release.gpg [198 B]          
Get:16 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                    
Get:17 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free TranslationIndex            
Get:18 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                    
Get:19 [http://mirror01.th.ifl.net](http://mirror01.th.ifl.net) precise-security Release.gpg [198 B]         
Get:20 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                    
Get:21 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                    
Get:22 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                    
Get:23 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                    
Get:24 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                    
Get:25 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Get:26 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                    
Get:27 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Get:28 [http://mirror01.th.ifl.net](http://mirror01.th.ifl.net) precise-security Release.gpg [198 B]         
Err [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
  Error reading from server - read (104: Connection reset by peer) [IP: 91.189.92.191 80]
Get:29 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                    
Get:30 [http://mirror01.th.ifl.net](http://mirror01.th.ifl.net) precise-security Release.gpg [198 B]         
Get:31 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                    
Get:32 [http://mirror01.th.ifl.net](http://mirror01.th.ifl.net) precise-security Release.gpg [198 B]         
Get:33 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                    
Get:34 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Err [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
  Error reading from server - read (104: Connection reset by peer) [IP: 91.189.92.191 80]
Get:35 [http://mirror01.th.ifl.net](http://mirror01.th.ifl.net) precise-backports Release.gpg [198 B]
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Get:36 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                    
Get:37 [http://mirror01.th.ifl.net](http://mirror01.th.ifl.net) precise-backports Release.gpg [198 B]        
Get:38 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                    
Get:39 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                    
Hit [http://mirror01.th.ifl.net](http://mirror01.th.ifl.net) precise Release                                 
Ign [http://mirror01.th.ifl.net](http://mirror01.th.ifl.net) precise Release                                 
E: GPG error: [http://mirror01.th.ifl.net](http://mirror01.th.ifl.net) precise Release: The following signatures were invalid: NODATA 2

Even my ubuntu software center has no install option what could be the problem ?

---

### Post by cwsnyder on 2012-11-18
According to your listing, one mirror you are using to download packages ([http://mirror01.th.ifl.net](http://mirror01.th.ifl.net)) is not responding.  You will probably have to wait for the mirror to come back up, or manually change your /etc/sources.list to point to a valid mirror for the packages you were trying to update.

---

