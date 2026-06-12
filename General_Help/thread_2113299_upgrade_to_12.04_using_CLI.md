---
title: "upgrade to 12.04 using CLI"
date: 2013-02-07
forum: General Help
---

### Post by travalon on 2013-02-07
If I follow the server instructions found here:
[https://help.ubuntu.com/community/PreciseUpgrades#Network_Upgrade_for_Ubuntu_Servers_.28Recommended.29](https://help.ubuntu.com/community/PreciseUpgrades#Network_Upgrade_for_Ubuntu_Servers_.28Recommended.29)

Will I get 12.04 or 12.10 when I upgrade from 11.10?


I am trying to get a XBMCbuntu comprised of 12.04 and  xbmc 12 Frodo.

If i run the command:  do-release-upgrade

I get this:   (hope the code wrap works)

```
travalon@XBMCenter:~$ sudo do-release-upgrade
[sudo] password for travalon: 
Checking for a new ubuntu release
Get:1 Upgrade tool signature [198 B]                                                                                                                         
Get:2 Upgrade tool [1551 kB]                                                                                                                                 
Fetched 1551 kB in 0s (0 B/s)                                                                                                                                
authenticate 'precise.tar.gz' against 'precise.tar.gz.gpg' 
extracting 'precise.tar.gz'

Reading cache

Checking package manager
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Building data structures... Done 
Ign http://us.archive.ubuntu.com oneiric InRelease                                                                                                           
Ign http://us.archive.ubuntu.com oneiric-updates InRelease                                                                                                   
Ign http://us.archive.ubuntu.com oneiric-backports InRelease                                                                                                 
Ign http://security.ubuntu.com oneiric-security InRelease                                                                                                    
Hit http://us.archive.ubuntu.com oneiric Release.gpg                                                                                                         
Get:1 http://us.archive.ubuntu.com oneiric-updates Release.gpg [198 B]                                                                                       
Get:2 http://security.ubuntu.com oneiric-security Release.gpg [198 B]                                                                                        
Get:3 http://security.ubuntu.com oneiric-security Release [40.8 kB]                                                                                          
Hit http://us.archive.ubuntu.com oneiric-backports Release.gpg                                                                                               
Ign http://ppa.launchpad.net oneiric InRelease                                                                                                               
Hit http://us.archive.ubuntu.com oneiric Release                                                                                                             
Hit http://ppa.launchpad.net oneiric Release.gpg                                                                                                             
Get:4 http://us.archive.ubuntu.com oneiric-updates Release [40.8 kB]                                                                                         
Get:5 http://security.ubuntu.com oneiric-security/main Sources [66.8 kB]                                                                                     
Ign http://www.lonelycoder.com hts InRelease                                                                                                                 
Hit http://ppa.launchpad.net oneiric Release                                                                                                                 
Hit http://us.archive.ubuntu.com oneiric-backports Release                                                                                                   
Hit http://www.lonelycoder.com hts Release.gpg                                                                                                               
Hit http://ppa.launchpad.net oneiric/main i386 Packages                                                                                                      
Hit http://us.archive.ubuntu.com oneiric/main Sources                                                                                                        
Hit http://us.archive.ubuntu.com oneiric/restricted Sources                                                                                                  
Hit http://us.archive.ubuntu.com oneiric/universe Sources                                                                                                    
Hit http://us.archive.ubuntu.com oneiric/multiverse Sources                                                                                                  
Hit http://us.archive.ubuntu.com oneiric/main i386 Packages                                                                                                  
Hit http://us.archive.ubuntu.com oneiric/restricted i386 Packages                                                                                            
Hit http://us.archive.ubuntu.com oneiric/universe i386 Packages                                                                                              
Hit http://us.archive.ubuntu.com oneiric/multiverse i386 Packages                                                                                            
Get:6 http://security.ubuntu.com oneiric-security/restricted Sources [1964 B]                                                                                
Get:7 http://security.ubuntu.com oneiric-security/universe Sources [26.7 kB]                                                                                 
Get:8 http://security.ubuntu.com oneiric-security/multiverse Sources [1684 B]                                                                                
Get:9 http://security.ubuntu.com oneiric-security/main i386 Packages [239 kB]                                                                                
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex                                                                                               
Hit http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex                                                                                         
Hit http://us.archive.ubuntu.com oneiric/restricted TranslationIndex                                                                                         
Hit http://us.archive.ubuntu.com oneiric/universe TranslationIndex                                                                                           
Get:10 http://us.archive.ubuntu.com oneiric-updates/main Sources [168 kB]                                                                                    
Hit http://www.lonelycoder.com hts Release                                                                                                                   
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                                                                                                   
Hit http://www.lonelycoder.com hts/main i386 Packages                                                                                                        
Err http://ppa.launchpad.net oneiric/main Translation-en                                                                                                     
                                                                                                                                                             
Err http://ppa.launchpad.net oneiric/main Translation-en                                                                                                     
                                                                                                                                                             
Ign http://www.lonelycoder.com hts/main TranslationIndex                                                                                                     
Get:11 http://security.ubuntu.com oneiric-security/restricted i386 Packages [4062 B]                                                                         
Get:12 http://security.ubuntu.com oneiric-security/universe i386 Packages [65.3 kB]                                                                          
Get:13 http://us.archive.ubuntu.com oneiric-updates/restricted Sources [3349 B]                                                                              
Get:14 http://us.archive.ubuntu.com oneiric-updates/universe Sources [69.3 kB]                                                                               
Err http://ppa.launchpad.net oneiric/main Translation-en                                                                                                     
                                                                                                                                                             
Err http://www.lonelycoder.com hts/main Translation-en                                                                                                       
                                                                                                                                                             
Get:15 http://security.ubuntu.com oneiric-security/multiverse i386 Packages [3386 B]                                                                         
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex                                                                                        
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex                                                                                  
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex                                                                                  
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex                                                                                    
Get:16 http://us.archive.ubuntu.com oneiric-updates/multiverse Sources [3703 B]                                                                              
Hit http://security.ubuntu.com oneiric-security/main Translation-en                                                                                          
Get:17 http://us.archive.ubuntu.com oneiric-updates/main i386 Packages [432 kB]                                                                              
Err http://ppa.launchpad.net oneiric/main Translation-en                                                                                                     
                                                                                                                                                             
Err http://www.lonelycoder.com hts/main Translation-en                                                                                                       
                                                                                                                                                             
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en                                                                                    
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en                                                                                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                                                                                                     
Hit http://security.ubuntu.com oneiric-security/universe Translation-en                                                                                      
Err http://www.lonelycoder.com hts/main Translation-en                                                                                                       
                                                                                                                                                             
Err http://www.lonelycoder.com hts/main Translation-en                                                                                                       
                                                                                                                                                             
Get:18 http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages [6645 B]                                                                        
Get:19 http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages [146 kB]                                                                          
Ign http://www.lonelycoder.com hts/main Translation-en                                                                                                       
Get:20 http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages [6371 B]                                                                        
Hit http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex                                                                                       
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex                                                                                 
Hit http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex                                                                                 
Hit http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex                                                                                   
Hit http://us.archive.ubuntu.com oneiric-backports/main Sources                                                                                              
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Sources                                                                                        
Hit http://us.archive.ubuntu.com oneiric-backports/universe Sources                                                                                          
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Sources                                                                                        
Hit http://us.archive.ubuntu.com oneiric-backports/main i386 Packages                                                                                        
Hit http://us.archive.ubuntu.com oneiric-backports/restricted i386 Packages                                                                                  
Hit http://us.archive.ubuntu.com oneiric-backports/universe i386 Packages                                                                                    
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse i386 Packages                                                                                  
Hit http://us.archive.ubuntu.com oneiric-backports/main TranslationIndex                                                                                     
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex                                                                               
Hit http://us.archive.ubuntu.com oneiric-backports/restricted TranslationIndex                                                                               
Hit http://us.archive.ubuntu.com oneiric-backports/universe TranslationIndex                                                                                 
Hit http://us.archive.ubuntu.com oneiric/main Translation-en                                                                                                 
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en                                                                                           
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en                                                                                           
Hit http://us.archive.ubuntu.com oneiric/universe Translation-en                                                                                             
Hit http://us.archive.ubuntu.com oneiric-updates/main Translation-en                                                                                         
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en                                                                                   
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en                                                                                   
Hit http://us.archive.ubuntu.com oneiric-updates/universe Translation-en                                                                                     
Hit http://us.archive.ubuntu.com oneiric-backports/main Translation-en                                                                                       
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en                                                                                 
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en                                                                                 
Hit http://us.archive.ubuntu.com oneiric-backports/universe Translation-en                                                                                   
Fetched 1326 kB in 0s (0 B/s)                                                                                                                                
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 

Updating repository information
WARNING: Failed to read mirror file

Third party sources disabled 

Some third party entries in your sources.list were disabled. You can 
re-enable them after the upgrade with the 'software-properties' tool 
or your package manager. 

To continue please press [ENTER]
```

---

### Post by carl4926 on 2013-02-07
A dist-upgrade will provide whatever sources you edit in

whatever you do, backup first

---

### Post by travalon on 2013-02-07
> **carl4926 said:**
> A dist-upgrade will provide whatever sources you edit in

whatever you do, backup first
I've never done anything like this before. How would, exactly, I edit in to get 12.04?
What would the command line be?

Thank you for your help.

---

### Post by carl4926 on 2013-02-07
There are guides
eg: [http://www.unixmen.com/how-to-upgrade-from-ubuntu-1004-1010-1104-to-ubuntu-1110-oneiric-ocelot-desktop-a-server/](http://www.unixmen.com/how-to-upgrade-from-ubuntu-1004-1010-1104-to-ubuntu-1110-oneiric-ocelot-desktop-a-server/)

---

### Post by Cheesemill on 2013-02-07
If you follow the instructions that you linked to you will be upgraded to 12.04.

You can only ever upgrade by one release at a time, with the exception of LTS releases which allow you to upgrade directly to the next LTS (10.04 > 12.04 for example).

---

### Post by travalon on 2013-02-07
Thanks for the link carl. I found that one but don't want 12.10.
Cheesemill, I didn't know only 1 release at a time thanks.

LTS XBMCbuntu might be good.

---

