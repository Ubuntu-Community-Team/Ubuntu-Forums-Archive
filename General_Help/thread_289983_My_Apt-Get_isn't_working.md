---
title: "My Apt-Get isn't working"
date: 2006-10-31
forum: General Help
---

### Post by hopspitfire on 2006-10-31
Most of my repositories won't update (it used to take a minute or two to update, now just a few seconds, on the same connection -> Fetched 11B in 1s (6B/s)), and I haven't been able to upgrade any packages since edgy went stable. Any help?


```
hopspitfire@zeeftw:~$ sudo apt-get update
Password:
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-en_US
Get:1 http://media.blutkind.org edgy Release.gpg [189B]                        
Ign http://media.blutkind.org edgy/main-edgy Translation-en_US                 
Get:2 http://www.beerorkid.com edgy Release.gpg [189B]                         
Hit http://media.blutkind.org edgy Release                                     
Ign http://media.blutkind.org edgy/main-edgy Packages                          
Hit http://media.blutkind.org edgy/main-edgy Packages                          
Get:3 http://www.getautomatix.com edgy Release.gpg [189B]                      
Ign http://www.getautomatix.com edgy/main Translation-en_US                    
Hit http://www.getautomatix.com edgy Release                                   
Ign http://www.beerorkid.com edgy/main-edgy Translation-en_US                  
Get:4 http://ubuntu.compiz.net edgy Release.gpg [189B]                         
Ign http://ubuntu.compiz.net edgy/main-edgy Translation-en_US                  
Get:5 http://archive.ubuntu.com edgy Release.gpg [191B]                        
Ign http://archive.ubuntu.com edgy/main Translation-en_US                      
Get:6 http://compiz-mirror.lupine.me.uk edgy Release.gpg [189B]                
Ign http://compiz-mirror.lupine.me.uk edgy/main-edgy Translation-en_US         
Ign http://amaranth.selfip.com edgy Release.gpg                                
Hit http://www.getautomatix.com edgy/main Packages                             
Get:7 http://archive.canonical.com dapper-commercial Release.gpg [191B]        
Ign http://archive.canonical.com dapper-commercial/main Translation-en_US      
Get:8 http://archive.canonical.com edgy-commercial Release.gpg [191B]          
Hit http://www.beerorkid.com edgy Release                                      
Hit http://ubuntu.compiz.net edgy Release                                      
Ign http://archive.ubuntu.com edgy/restricted Translation-en_US                
Ign http://archive.ubuntu.com edgy/universe Translation-en_US                  
Ign http://archive.ubuntu.com edgy/multiverse Translation-en_US                
Hit http://compiz-mirror.lupine.me.uk edgy Release                             
Ign http://www.beerorkid.com edgy/main-edgy Packages                           
Get:9 http://archive.ubuntu.com edgy-security Release.gpg [189B]               
Ign http://archive.ubuntu.com edgy-security/main Translation-en_US             
Ign http://archive.ubuntu.com edgy-security/restricted Translation-en_US       
Hit http://www.beerorkid.com edgy/main-edgy Packages                           
Ign http://archive.canonical.com edgy-commercial/main Translation-en_US        
Hit http://archive.canonical.com dapper-commercial Release                     
Ign http://archive.ubuntu.com edgy-security/universe Translation-en_US         
Ign http://archive.ubuntu.com edgy-security/multiverse Translation-en_US       
Get:10 http://archive.ubuntu.com edgy-updates Release.gpg [189B]               
Ign http://ubuntu.compiz.net edgy/main-edgy Packages                           
Ign http://amaranth.selfip.com edgy/lrm Translation-en_US                      
Ign http://compiz-mirror.lupine.me.uk edgy/main-edgy Packages                  
Ign http://archive.ubuntu.com edgy-updates/main Translation-en_US              
Hit http://archive.canonical.com edgy-commercial Release                       
Ign http://archive.ubuntu.com edgy-updates/restricted Translation-en_US        
Ign http://archive.ubuntu.com edgy-updates/universe Translation-en_US          
Ign http://archive.ubuntu.com edgy-updates/multiverse Translation-en_US        
Hit http://ubuntu.compiz.net edgy/main-edgy Packages                           
Hit http://compiz-mirror.lupine.me.uk edgy/main-edgy Packages                  
Get:11 http://archive.ubuntu.com edgy-backports Release.gpg [189B]             
Ign http://archive.ubuntu.com edgy-backports/main Translation-en_US  
Ign http://archive.ubuntu.com edgy-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com edgy-backports/universe Translation-en_US
Ign http://archive.ubuntu.com edgy-backports/multiverse Translation-en_US
Hit http://archive.ubuntu.com edgy Release                           
Hit http://archive.canonical.com dapper-commercial/main Packages               
Ign http://amaranth.selfip.com edgy Release                                    
Hit http://archive.ubuntu.com edgy-security Release                  
Hit http://archive.ubuntu.com edgy-updates Release                             
Hit http://archive.canonical.com edgy-commercial/main Packages                 
Hit http://archive.ubuntu.com edgy-backports Release                           
Ign http://amaranth.selfip.com edgy/lrm Packages                              
Hit http://archive.ubuntu.com edgy/main Packages
Hit http://archive.ubuntu.com edgy/restricted Packages
Hit http://archive.ubuntu.com edgy/universe Packages
Hit http://archive.ubuntu.com edgy/multiverse Packages
Hit http://archive.ubuntu.com edgy-security/main Packages
Hit http://archive.ubuntu.com edgy-security/restricted Packages               
Hit http://archive.ubuntu.com edgy-security/universe Packages                 
Hit http://archive.ubuntu.com edgy-security/multiverse Packages               
Hit http://archive.ubuntu.com edgy-updates/main Packages
Hit http://archive.ubuntu.com edgy-updates/restricted Packages
Hit http://archive.ubuntu.com edgy-updates/universe Packages
Hit http://archive.ubuntu.com edgy-updates/multiverse Packages
Hit http://archive.ubuntu.com edgy-backports/main Packages
Hit http://archive.ubuntu.com edgy-backports/restricted Packages
Hit http://amaranth.selfip.com edgy/lrm Packages
Hit http://archive.ubuntu.com edgy-backports/universe Packages
Hit http://archive.ubuntu.com edgy-backports/multiverse Packages
Fetched 11B in 1s (6B/s) 
Reading package lists... Done

```

---

### Post by PriceChild on 2006-10-31
Probably because there haven't been any packages to update...

---

### Post by hopspitfire on 2006-10-31
> **PriceChild said:**
> Probably because there haven't been any packages to update...

but I remember the last distribution, when dapper came out there were many updates the first 2 weeks, just wondering if my system is normal

---

### Post by pbaehr on 2006-10-31
I haven't seen any updates yet, either. I'm pretty sure there just haven't been any.

Also, when you run apt-get update it doesn't need to download anything if no changes were made to the repositories so it will go faster after the first run. At least that's my understanding.

Anyway, if the update was failing it would give you an error. Yours looks perfectly functional.

---

