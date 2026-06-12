---
title: "ppa.launchpad.net wily/main i386 Packages; Missing Even After Today's Source Updates"
date: 2015-11-13
forum: General Help
---

### Post by alexel2 on 2015-11-13
It is just as stated. Any help would be greatly appreciated since I still have MUCH to learn. I have checked the my source permissions, launchpad updates, Ubuntu/Kubuntu notes, but still cannot seem to find the problem. My report for  sudo apt-get update is as follows:


```

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily InRelease
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-updates InRelease [64.4 kB]                         
Hit [http://archive.canonical.com](http://archive.canonical.com) wily InRelease                                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily InRelease                                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily InRelease                                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily InRelease                                                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) wily InRelease                                                               
Hit [http://archive.canonical.com](http://archive.canonical.com) wily/partner Sources                            
Hit [http://archive.canonical.com](http://archive.canonical.com) wily/partner i386 Packages                      
Ign [http://archive.canonical.com](http://archive.canonical.com) wily/partner Translation-en                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) wily Release.gpg                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main i386 Packages                       
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-security InRelease [64.4 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Translation-en     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main i386 Packages       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main i386 Packages                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Translation-en      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) wily Release                  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main i386 Packages       
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Translation-en_US   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-backports InRelease                                                    
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-updates/main Sources [16.8 kB]                                       
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-updates/restricted Sources [28 B]                                    
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-updates/universe Sources [4,272 B]                                   
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-updates/multiverse Sources [725 B]                                   
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-updates/main i386 Packages [43.1 kB]                                 
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-updates/restricted i386 Packages [28 B]                              
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-updates/universe i386 Packages [15.2 kB]                             
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-updates/multiverse i386 Packages [1,408 B]                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-updates/restricted Translation-en                                      
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-security/main Sources [13.2 kB]                                     
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-security/restricted Sources [28 B]                                  
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-security/universe Sources [2,496 B]                                 
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-security/multiverse Sources [725 B]                                 
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-security/main i386 Packages [34.0 kB]                               
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-security/restricted i386 Packages [28 B]                            
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-security/universe i386 Packages [13.3 kB]                           
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-security/multiverse i386 Packages [1,408 B]                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-security/restricted Translation-en                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-backports/restricted i386 Packages                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-backports/main i386 Packages                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-backports/universe i386 Packages                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-backports/multiverse i386 Packages                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-backports/main Translation-en                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-backports/multiverse Translation-en                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-backports/restricted Translation-en                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-backports/universe Translation-en                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/main Sources                                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/restricted Sources                                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/universe Sources                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/multiverse Sources                                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/main i386 Packages                                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/restricted i386 Packages                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/universe i386 Packages                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/multiverse i386 Packages                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/main Translation-en                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/multiverse Translation-en                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/restricted Translation-en                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily/universe Translation-en                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-updates/main Translation-en                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-updates/multiverse Translation-en                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-updates/universe Translation-en                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-security/main Translation-en                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-security/multiverse Translation-en                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-security/universe Translation-en                                       
Fetched 276 kB in 23s (11.7 kB/s)                                                                            
W: Failed to fetch [http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu/dists/wily/main/binary-i386/Packages](http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu/dists/wily/main/binary-i386/Packages)  404  Not Found
```



Thank you!

---

### Post by deadflowr on 2015-11-13
There is no such ppa.
the kdenlive-release ppa only goes to vivid.
You'll need to disable it, for wiy, for now.

---

### Post by alexel2 on 2015-11-14
Thank you, a lot. I'll be sure to check more closely next time.

---

### Post by Lostwon on 2015-12-20
EDIT:
To disable this source open Software & updates from Applications>System Tools>... 

In Software & Updates switch to the Other Software Tab

Scroll down the list until you see the offending source and uncheck it.  

Thanks guys!

Sorry to bring up an old thread, but I need to know where or how I can disable this.  It doesn't seem to be via the /ext/apt/sources.lst.d or /ext/apt/sources.list.  I am not sure, but it seems to cause the Intel Graphics Installer for Linux to quit with an error when it encounters this.
Thank you greatly. I am running ubuntu 15.10 on GNOME 3.16.2 on Kernel 4.20-21-generic.
Thank you.

---

