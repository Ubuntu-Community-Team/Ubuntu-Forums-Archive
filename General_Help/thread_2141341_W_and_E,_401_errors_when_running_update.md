---
title: "W and E, 401 errors when running update"
date: 2013-05-02
forum: General Help
---

### Post by wesy2kn1 on 2013-05-02
Well this one is over my head guys...before I confuse myself more than I already have, here is what I'm getting.

```
$ sudo apt-get update&&sudo apt-get upgrade
[sudo] password for wesy2kn1: 
Hit http://us.archive.ubuntu.com raring Release.gpg
Hit http://us.archive.ubuntu.com raring-updates Release.gpg                    
Hit http://dl.google.com stable Release.gpg                                    
Get:1 http://us.archive.ubuntu.com raring-backports Release.gpg [933 B]        
Hit http://security.ubuntu.com raring-security Release.gpg                     
Hit http://archive.canonical.com raring Release.gpg                            
Hit http://extras.ubuntu.com raring Release.gpg                                
Hit http://ppa.launchpad.net raring Release.gpg                                
Hit http://dl.google.com stable Release                                        
Hit http://repo.steampowered.com precise Release.gpg                           
Hit http://archive.ubuntu.com raring Release.gpg                               
Hit http://us.archive.ubuntu.com raring Release                                
Hit http://us.archive.ubuntu.com raring-updates Release                        
Hit http://repo.steampowered.com precise Release                               
Hit http://archive.canonical.com raring Release                                
Hit http://security.ubuntu.com raring-security Release                         
Hit http://ppa.launchpad.net raring Release.gpg                                
Hit http://archive.ubuntu.com raring Release                                   
Hit http://extras.ubuntu.com raring Release                                    
Get:2 http://us.archive.ubuntu.com raring-backports Release [40.8 kB]          
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://repo.steampowered.com precise/steam Sources                         
Hit http://ppa.launchpad.net raring Release.gpg                                
Hit http://archive.canonical.com raring/partner Sources                        
Hit http://security.ubuntu.com raring-security/main Sources                    
Hit http://us.archive.ubuntu.com raring/main Sources                           
Hit http://archive.ubuntu.com raring/main Sources                              
Hit http://extras.ubuntu.com raring/main Sources                               
Hit http://us.archive.ubuntu.com raring/multiverse Sources                     
Hit http://ppa.launchpad.net raring Release                                    
Hit http://us.archive.ubuntu.com raring/restricted Sources                     
Hit http://security.ubuntu.com raring-security/multiverse Sources              
Hit http://repo.steampowered.com precise/steam amd64 Packages                  
Hit http://us.archive.ubuntu.com raring/universe Sources                       
Hit http://archive.ubuntu.com raring/restricted Sources                        
Hit http://extras.ubuntu.com raring/main amd64 Packages                        
Hit http://ppa.launchpad.net raring Release                                    
Hit http://us.archive.ubuntu.com raring/main amd64 Packages                    
Hit http://security.ubuntu.com raring-security/restricted Sources              
Hit http://us.archive.ubuntu.com raring/restricted amd64 Packages              
Hit http://extras.ubuntu.com raring/main i386 Packages                         
Hit http://us.archive.ubuntu.com raring/universe amd64 Packages                
Hit http://ppa.launchpad.net raring Release                                    
Hit http://us.archive.ubuntu.com raring/multiverse amd64 Packages              
Hit http://repo.steampowered.com precise/steam i386 Packages                   
Hit http://security.ubuntu.com raring-security/universe Sources                
Get:3 https://private-ppa.launchpad.net raring Release.gpg [493 B]             
Ign https://private-ppa.launchpad.net raring Release.gpg                       
Hit http://us.archive.ubuntu.com raring/main i386 Packages                     
Hit http://ppa.launchpad.net raring/main amd64 Packages                        
Hit http://us.archive.ubuntu.com raring/restricted i386 Packages               
Hit http://security.ubuntu.com raring-security/main amd64 Packages             
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://ppa.launchpad.net raring/main i386 Packages                         
Ign http://dl.google.com stable/main Translation-en                            
Hit http://us.archive.ubuntu.com raring/universe i386 Packages                 
Hit http://security.ubuntu.com raring-security/restricted amd64 Packages       
Hit http://us.archive.ubuntu.com raring/multiverse i386 Packages               
Hit http://security.ubuntu.com raring-security/universe amd64 Packages         
Hit http://us.archive.ubuntu.com raring/main Translation-en                    
Hit http://us.archive.ubuntu.com raring/multiverse Translation-en              
Hit http://security.ubuntu.com raring-security/multiverse amd64 Packages       
Hit http://ppa.launchpad.net raring/main amd64 Packages              
Hit http://us.archive.ubuntu.com raring/restricted Translation-en              
Hit http://security.ubuntu.com raring-security/main i386 Packages              
Hit https://private-ppa.launchpad.net raring Release.gpg                       
Hit http://us.archive.ubuntu.com raring/universe Translation-en                
Hit http://ppa.launchpad.net raring/main i386 Packages                         
Hit http://us.archive.ubuntu.com raring-updates/main Sources                   
Hit http://security.ubuntu.com raring-security/restricted i386 Packages        
Get:4 https://private-ppa.launchpad.net raring Release.gpg [493 B]             
Ign https://private-ppa.launchpad.net raring Release.gpg                       
Hit http://us.archive.ubuntu.com raring-updates/multiverse Sources             
Hit http://us.archive.ubuntu.com raring-updates/restricted Sources             
Hit http://security.ubuntu.com raring-security/universe i386 Packages          
Hit http://us.archive.ubuntu.com raring-updates/universe Sources     
Hit http://us.archive.ubuntu.com raring-updates/main amd64 Packages  
Hit http://us.archive.ubuntu.com raring-updates/restricted amd64 Packages      
Hit http://security.ubuntu.com raring-security/multiverse i386 Packages        
Hit http://us.archive.ubuntu.com raring-updates/universe amd64 Packages        
Hit http://ppa.launchpad.net raring/main amd64 Packages                        
Ign http://extras.ubuntu.com raring/main Translation-en_US                     
Hit http://us.archive.ubuntu.com raring-updates/multiverse amd64 Packages      
Hit http://ppa.launchpad.net raring/main i386 Packages                         
Ign http://extras.ubuntu.com raring/main Translation-en                        
Hit http://us.archive.ubuntu.com raring-updates/main i386 Packages   
Hit http://security.ubuntu.com raring-security/main Translation-en   
Hit http://us.archive.ubuntu.com raring-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com raring-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com raring-updates/multiverse i386 Packages
Ign https://private-ppa.launchpad.net raring Release                 
Hit http://us.archive.ubuntu.com raring-updates/main Translation-en            
Hit http://us.archive.ubuntu.com raring-updates/multiverse Translation-en      
Hit http://us.archive.ubuntu.com raring-updates/restricted Translation-en
Hit http://security.ubuntu.com raring-security/multiverse Translation-en
Ign http://repo.steampowered.com precise/steam Translation-en_US     
Hit http://us.archive.ubuntu.com raring-updates/universe Translation-en
Get:5 http://us.archive.ubuntu.com raring-backports/main Sources [14 B]        
Ign http://repo.steampowered.com precise/steam Translation-en                  
Get:6 http://us.archive.ubuntu.com raring-backports/restricted Sources [14 B]  
Get:7 http://us.archive.ubuntu.com raring-backports/universe Sources [1,618 B] 
Hit http://security.ubuntu.com raring-security/restricted Translation-en       
Get:8 http://us.archive.ubuntu.com raring-backports/multiverse Sources [14 B]  
Hit https://private-ppa.launchpad.net raring Release                      
Get:9 http://us.archive.ubuntu.com raring-backports/main amd64 Packages [14 B] 
Get:10 https://private-ppa.launchpad.net raring Release [493 B]                
Get:11 http://us.archive.ubuntu.com raring-backports/restricted amd64 Packages [14 B]
Ign https://private-ppa.launchpad.net raring Release                           
Hit http://security.ubuntu.com raring-security/universe Translation-en         
Get:12 http://us.archive.ubuntu.com raring-backports/universe amd64 Packages [2,155 B]
Get:13 http://us.archive.ubuntu.com raring-backports/multiverse amd64 Packages [14 B]
Get:14 http://us.archive.ubuntu.com raring-backports/main i386 Packages [14 B]
Get:15 http://us.archive.ubuntu.com raring-backports/restricted i386 Packages [14 B]
Get:16 http://us.archive.ubuntu.com raring-backports/universe i386 Packages [2,178 B]
Get:17 http://us.archive.ubuntu.com raring-backports/multiverse i386 Packages [14 B]
Hit http://us.archive.ubuntu.com raring-backports/main Translation-en          
Hit http://us.archive.ubuntu.com raring-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com raring-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com raring-backports/universe Translation-en
Ign http://security.ubuntu.com raring-security/main Translation-en_US
Ign http://security.ubuntu.com raring-security/multiverse Translation-en_US
Ign http://ppa.launchpad.net raring/main Translation-en_US           
Ign http://security.ubuntu.com raring-security/restricted Translation-en_US
Ign http://ppa.launchpad.net raring/main Translation-en              
Ign http://security.ubuntu.com raring-security/universe Translation-en_US
Ign http://ppa.launchpad.net raring/main Translation-en_US           
Ign http://ppa.launchpad.net raring/main Translation-en
Ign http://ppa.launchpad.net raring/main Translation-en_US
Ign http://ppa.launchpad.net raring/main Translation-en
Ign http://us.archive.ubuntu.com raring/main Translation-en_US
Ign http://us.archive.ubuntu.com raring/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com raring/restricted Translation-en_US
Ign http://us.archive.ubuntu.com raring/universe Translation-en_US
Ign http://us.archive.ubuntu.com raring-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com raring-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com raring-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com raring-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com raring-backports/main Translation-en_US
Hit https://private-ppa.launchpad.net raring/main amd64 Packages
Ign http://us.archive.ubuntu.com raring-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com raring-backports/restricted Translation-en_US
Hit https://private-ppa.launchpad.net raring/main i386 Packages
Ign http://us.archive.ubuntu.com raring-backports/universe Translation-en_US
Get:18 https://private-ppa.launchpad.net raring/main amd64 Packages [493 B]    
Err https://private-ppa.launchpad.net raring/main amd64 Packages               
  The requested URL returned error: 401
Err https://private-ppa.launchpad.net raring/main i386 Packages
  The requested URL returned error: 401
Ign https://private-ppa.launchpad.net raring/main Translation-en_US
Ign https://private-ppa.launchpad.net raring/main Translation-en
Ign https://private-ppa.launchpad.net raring/main Translation-en_US
Ign https://private-ppa.launchpad.net raring/main Translation-en
Err https://private-ppa.launchpad.net raring/main amd64 Packages
  The requested URL returned error: 401
Err https://private-ppa.launchpad.net raring/main i386 Packages
  The requested URL returned error: 401
Ign https://private-ppa.launchpad.net raring/main Translation-en_US
Ign https://private-ppa.launchpad.net raring/main Translation-en
Fetched 47.8 kB in 29s (1,608 B/s)
W: Failed to fetch https://private-ppa.launchpad.net/commercial-ppa-uploaders/nitro/ubuntu/dists/raring/main/binary-amd64/Packages  The requested URL returned error: 401

W: Failed to fetch https://private-ppa.launchpad.net/commercial-ppa-uploaders/nitro/ubuntu/dists/raring/main/binary-i386/Packages  The requested URL returned error: 401

W: Failed to fetch https://private-ppa.launchpad.net/commercial-ppa-uploaders/stormcloud/ubuntu/dists/raring/main/binary-amd64/Packages  The requested URL returned error: 401

W: Failed to fetch https://private-ppa.launchpad.net/commercial-ppa-uploaders/stormcloud/ubuntu/dists/raring/main/binary-i386/Packages  The requested URL returned error: 401

E: Some index files failed to download. They have been ignored, or old ones used instead.
wesy2kn1@ELIULT-001:~$ 

```

Can someone educate me on what's going on here and how do I fix this?

Thanks in advance!

---

### Post by ibjsb4 on 2013-05-02
I cannot verify a private ppa, but you nee to check to see if there is a 13.04 release for it.  Theres a chance that it has not been updated yet.


[https://private-ppa.launchpad.net/commercial-ppa-uploaders/stormcloud/ubuntu/dists/](https://private-ppa.launchpad.net/commercial-ppa-uploaders/stormcloud/ubuntu/dists/)

---

### Post by wesy2kn1 on 2013-05-02
Well. It appears that the software I purchased and had issues downloading last night was the issue. Thanks for the good eyes. Now that brings up another issue with installing software center purchases on a new install...I've had nothing but trouble.

---

### Post by ibjsb4 on 2013-05-02
Got me on that one, I do not use the service.  Not sure if your can, but maybe edit your thread title to include "software center purchases".  Should help to draw the right crowd.  Good luck :)

EDIT:  just seen the "solved" in the title.  Maybe just start another thread on it.

---

### Post by wesy2kn1 on 2013-05-02
Yeah, I didn't want the thread to meander by starting at one question and ending in another! haha thanks for the help!

---

