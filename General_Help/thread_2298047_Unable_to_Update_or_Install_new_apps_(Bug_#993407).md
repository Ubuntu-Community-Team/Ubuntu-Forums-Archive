---
title: "Unable to Update or Install new apps (Bug #993407)"
date: 2015-10-08
forum: General Help
---

### Post by CampSoup1988 on 2015-10-08
My issues started earlier today when I ran the Software Updater on my  computer which is running the 64-bit version of Ubuntu 14.04.  The  update failed and redirected me to the bug tracker for Bug #993407 (You  can read it [HERE]("https://bugs.launchpad.net/ubuntu/+source/texinfo/+bug/993407") )

  I have since restarted my computer and tried the following commands:

```
sudo apt-get autoclean
```
Results:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done

```

```
sudo apt-get install -f
```
Results:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:[INDENT]libupstart1 linux-image-extra-3.13.0-30-generic   
[/INDENT]
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 84 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up install-info (5.2.0.dfsg.1-2) ...
/etc/environment: line 2: PATH: command not found
dpkg: error processing package install-info (--configure):[INDENT] subprocess installed post-installation script returned error exit status 127   
[/INDENT]
Errors were encountered while processing:[INDENT]install-info[/INDENT]
E: Sub-process /usr/bin/dpkg returned an error code (1)

 
```

I thank you in advance for any advice on how to resolve this issue.

---

### Post by CampSoup1988 on 2015-10-20
With some assistance from the Ubuntu IRC channel, I have done the following:

```
sudo apt-get update; lsb_release -a; uname -a
```

Results:

```
Ign http://dl.google.com stable InRelease
Ign http://dl.google.com stable InRelease                                      
Hit http://dl.google.com stable Release.gpg                                    
Hit http://dl.google.com stable Release.gpg                                    
Hit http://dl.google.com stable Release                                        
Ign http://www.openprinting.org lsb3.2 InRelease                               
Hit http://dl.google.com stable Release                                        
Hit http://www.openprinting.org lsb3.2 Release.gpg                             
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://www.openprinting.org lsb3.2 Release                                 
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://www.openprinting.org lsb3.2/contrib amd64 Packages                  
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://www.openprinting.org lsb3.2/contrib i386 Packages                   
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://www.openprinting.org lsb3.2/contrib Translation-en_US               
Hit http://www.openprinting.org lsb3.2/contrib Translation-en                  
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://archive.getdeb.net trusty-getdeb InRelease                          
Hit http://archive.getdeb.net trusty-getdeb/apps amd64 Packages                
Hit http://archive.getdeb.net trusty-getdeb/apps i386 Packages                 
Get:1 http://plex.r.worldssl.net lucid InRelease                               
Ign http://plex.r.worldssl.net lucid InRelease                                 
Ign http://plex.r.worldssl.net lucid Release.gpg                               
Ign http://plex.r.worldssl.net lucid Release                                   
Ign http://plex.r.worldssl.net lucid/main amd64 Packages/DiffIndex             
Ign http://plex.r.worldssl.net lucid/main i386 Packages/DiffIndex              
Err http://plex.r.worldssl.net lucid/main amd64 Packages                       
  
Err http://plex.r.worldssl.net lucid/main i386 Packages                        
  
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en_US             
Ign http://archive.canonical.com trusty InRelease                              
Err http://plex.r.worldssl.net lucid/main amd64 Packages                       
  
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.canonical.com trusty Release.gpg                            
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en                
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.canonical.com trusty Release                                
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:2 http://security.ubuntu.com trusty-security InRelease [64.4 kB]           
Hit http://archive.canonical.com trusty/partner Sources                        
Ign http://plex.r.worldssl.net lucid/main Translation-en_US                    
Hit http://ppa.launchpad.net trusty InRelease                                  
Ign http://plex.r.worldssl.net lucid/main Translation-en                       
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Err http://plex.r.worldssl.net lucid/main amd64 Packages                       
  HttpError404
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Err http://plex.r.worldssl.net lucid/main i386 Packages                        
  HttpError404
Hit http://ppa.launchpad.net trusty Release.gpg                                
Ign http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Ign http://archive.canonical.com trusty/partner Translation-en                 
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:3 http://security.ubuntu.com trusty-security/main Sources [97.7 kB]        
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Ign http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Get:4 http://security.ubuntu.com trusty-security/restricted Sources [3,357 B]  
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:5 http://security.ubuntu.com trusty-security/universe Sources [31.0 kB]    
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:6 http://security.ubuntu.com trusty-security/multiverse Sources [2,346 B]  
Get:7 http://security.ubuntu.com trusty-security/main amd64 Packages [356 kB]  
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://us.archive.ubuntu.com trusty InRelease                              
Hit http://us.archive.ubuntu.com trusty-updates InRelease                     
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://us.archive.ubuntu.com trusty-updates/main Sources                   
Hit http://us.archive.ubuntu.com trusty-updates/restricted Sources             
Hit http://us.archive.ubuntu.com trusty-updates/universe Sources               
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Sources             
Hit http://us.archive.ubuntu.com trusty-updates/main amd64 Packages            
Get:8 http://security.ubuntu.com trusty-security/restricted amd64 Packages [12.4 kB]
Hit http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages      
Hit http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages        
Get:9 http://security.ubuntu.com trusty-security/universe amd64 Packages [117 kB]
Hit http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages      
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-updates/main i386 Packages             
Err http://ppa.launchpad.net trusty/main amd64 Packages                        
  404  Not Found
Err http://ppa.launchpad.net trusty/main i386 Packages                         
  404  Not Found
Hit http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages       
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Hit http://us.archive.ubuntu.com trusty-updates/universe i386 Packages         
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Get:10 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [3,688 B]
Hit http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages       
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en            
Get:11 http://security.ubuntu.com trusty-security/main i386 Packages [338 kB]  
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en        
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Get:12 http://security.ubuntu.com trusty-security/restricted i386 Packages [12.2 kB]
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Get:13 http://security.ubuntu.com trusty-security/universe i386 Packages [117 kB]
Hit http://us.archive.ubuntu.com trusty/universe Sources                    
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Get:14 http://security.ubuntu.com trusty-security/multiverse i386 Packages [3,846 B]
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages  
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
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
Fetched 1,159 kB in 34s (33.8 kB/s)                                            
W: Failed to fetch http://plex.r.worldssl.net/PlexMediaServer/ubuntu-repo/dists/lucid/main/binary-amd64/Packages  HttpError404

W: Failed to fetch http://plex.r.worldssl.net/PlexMediaServer/ubuntu-repo/dists/lucid/main/binary-i386/Packages  HttpError404

W: Failed to fetch http://ppa.launchpad.net/mudlet-makers/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/mudlet-makers/ppa/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty
Linux Pantry 3.13.0-63-generic #103-Ubuntu SMP Fri Aug 14 21:42:59 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

I was then advised to remove the following to PPAs for the following reasons:

[http://ppa.launchpad.net/mudlet-makers/ppa/ubuntu](http://ppa.launchpad.net/mudlet-makers/ppa/ubuntu)
> doesn't support your release and should be removed
[http://plex.r.worldssl.net/PlexMediaServer/ubuntu-repo](http://plex.r.worldssl.net/PlexMediaServer/ubuntu-repo)
> it's still looking for the lucid folder. Lucid is EOL and not supported in any way

I then refreshed my package list using ```
sudo apt-get update
```

I then reran ```
sudo apt-get update; lsb_release -a; uname -a
``` and got the following results:

```
Ign http://dl.google.com stable InRelease
Ign http://us.archive.ubuntu.com trusty InRelease                              
Ign http://dl.google.com stable InRelease                                      
Hit http://security.ubuntu.com trusty-security InRelease                       
Hit http://us.archive.ubuntu.com trusty-updates InRelease                      
Ign http://archive.canonical.com trusty InRelease                              
Hit http://dl.google.com stable Release.gpg                                    
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://dl.google.com stable Release.gpg                                    
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Ign http://www.openprinting.org lsb3.2 InRelease                               
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://dl.google.com stable Release                                        
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://archive.getdeb.net trusty-getdeb InRelease                          
Hit http://dl.google.com stable Release                                        
Hit http://www.openprinting.org lsb3.2 Release.gpg                             
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.canonical.com trusty Release                                
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://security.ubuntu.com trusty-security/main Sources                    
Hit http://www.openprinting.org lsb3.2 Release                                 
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty-updates/main Sources                   
Hit http://security.ubuntu.com trusty-security/restricted Sources              
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://security.ubuntu.com trusty-security/universe Sources                
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://us.archive.ubuntu.com trusty-updates/restricted Sources             
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Hit http://us.archive.ubuntu.com trusty-updates/universe Sources               
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Sources             
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://archive.getdeb.net trusty-getdeb/apps amd64 Packages                
Hit http://www.openprinting.org lsb3.2/contrib amd64 Packages                  
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Hit http://us.archive.ubuntu.com trusty-updates/main amd64 Packages            
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Hit http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages      
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://www.openprinting.org lsb3.2/contrib i386 Packages                   
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://archive.getdeb.net trusty-getdeb/apps i386 Packages                 
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages       
Hit http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages        
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages      
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty-updates/main i386 Packages             
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages       
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Hit http://us.archive.ubuntu.com trusty-updates/universe i386 Packages         
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages       
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Ign http://archive.canonical.com trusty/partner Translation-en                 
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en        
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Ign http://dl.google.com stable/main Translation-en                            
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Ign http://dl.google.com stable/main Translation-en                            
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages              
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en_US             
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en                
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages    
Ign http://www.openprinting.org lsb3.2/contrib Translation-en_US               
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://www.openprinting.org lsb3.2/contrib Translation-en       
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en   
Hit http://ppa.launchpad.net trusty/main amd64 Packages             
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en 
Hit http://ppa.launchpad.net trusty/main Translation-en           
Hit http://us.archive.ubuntu.com trusty/universe Translation-en   
Ign http://ppa.launchpad.net trusty/main Translation-en_US                
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US            
Ign http://ppa.launchpad.net trusty/main Translation-en                  
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US    
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Reading package lists... Done                                                  
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty
Linux Pantry 3.13.0-63-generic #103-Ubuntu SMP Fri Aug 14 21:42:59 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


```

---

