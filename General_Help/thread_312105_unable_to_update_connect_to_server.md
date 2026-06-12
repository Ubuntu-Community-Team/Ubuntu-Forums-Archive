---
title: "unable to update/ connect to server"
date: 2006-12-03
forum: General Help
---

### Post by johnmxg12 on 2006-12-03
i havent been able to update my packages recently, within the past day or so, i made sure that i had permission to download all types of software in software sources.  

this is what i get when i type sudo apt-get update

```
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-en_US
Get:1 http://archive.ubuntu.com edgy-proposed Release.gpg [191B]               
Ign http://archive.ubuntu.com edgy-proposed/restricted Translation-en_US       
Get:2 http://security.ubuntu.com edgy-security Release.gpg [191B]              
Ign http://security.ubuntu.com edgy-security/main Translation-en_US            
Ign http://archive.ubuntu.com edgy-proposed/main Translation-en_US             
Ign http://archive.ubuntu.com edgy-proposed/multiverse Translation-en_US       
Ign http://archive.ubuntu.com edgy-proposed/universe Translation-en_US         
Get:3 http://archive.ubuntu.com edgy-backports Release.gpg [191B]              
Ign http://archive.ubuntu.com edgy-backports/restricted Translation-en_US      
Ign http://archive.ubuntu.com edgy-backports/main Translation-en_US            
Ign http://archive.ubuntu.com edgy-backports/multiverse Translation-en_US      
Ign http://archive.ubuntu.com edgy-backports/universe Translation-en_US        
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US      
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US        
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US      
Hit http://security.ubuntu.com edgy-security Release                           
Hit http://archive.ubuntu.com edgy-proposed Release                            
Hit http://archive.ubuntu.com edgy-backports Release                           
Hit http://security.ubuntu.com edgy-security/main Packages                     
Hit http://archive.ubuntu.com edgy-proposed/restricted Packages                
Hit http://archive.ubuntu.com edgy-proposed/main Packages                      
Hit http://archive.ubuntu.com edgy-proposed/multiverse Packages                
Hit http://security.ubuntu.com edgy-security/restricted Packages               
Hit http://security.ubuntu.com edgy-security/universe Packages                 
Hit http://security.ubuntu.com edgy-security/multiverse Packages               
Hit http://archive.ubuntu.com edgy-proposed/universe Packages                  
Hit http://archive.ubuntu.com edgy-proposed/restricted Sources                 
Hit http://archive.ubuntu.com edgy-proposed/main Sources                       
Hit http://archive.ubuntu.com edgy-proposed/multiverse Sources                 
Hit http://archive.ubuntu.com edgy-proposed/universe Sources                   
Hit http://archive.ubuntu.com edgy-backports/restricted Packages               
Hit http://archive.ubuntu.com edgy-backports/main Packages                     
Hit http://security.ubuntu.com edgy-security/main Sources                      
Hit http://security.ubuntu.com edgy-security/restricted Sources                
Hit http://security.ubuntu.com edgy-security/universe Sources                  
Hit http://security.ubuntu.com edgy-security/multiverse Sources                
Hit http://archive.ubuntu.com edgy-backports/multiverse Packages               
Hit http://archive.ubuntu.com edgy-backports/universe Packages                 
Hit http://archive.ubuntu.com edgy-backports/restricted Sources                
Hit http://archive.ubuntu.com edgy-backports/main Sources                      
Hit http://archive.ubuntu.com edgy-backports/multiverse Sources                
Hit http://archive.ubuntu.com edgy-backports/universe Sources                  
Ign http://us.archive.ubuntu.com edgy Release.gpg                              
Ign http://us.archive.ubuntu.com edgy/main Translation-en_US
Ign http://us.archive.ubuntu.com edgy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com edgy/universe Translation-en_US
Ign http://us.archive.ubuntu.com edgy/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates Release.gpg
Ign http://us.archive.ubuntu.com edgy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com edgy Release
Ign http://us.archive.ubuntu.com edgy-updates Release
Ign http://us.archive.ubuntu.com edgy/main Packages
Ign http://us.archive.ubuntu.com edgy/restricted Packages
Ign http://us.archive.ubuntu.com edgy/universe Packages
Ign http://us.archive.ubuntu.com edgy/multiverse Packages
Ign http://us.archive.ubuntu.com edgy/main Sources
Ign http://us.archive.ubuntu.com edgy/restricted Sources
Ign http://us.archive.ubuntu.com edgy/universe Sources
Ign http://us.archive.ubuntu.com edgy/multiverse Sources
Ign http://us.archive.ubuntu.com edgy-updates/main Packages
Ign http://us.archive.ubuntu.com edgy-updates/restricted Packages
Ign http://us.archive.ubuntu.com edgy-updates/universe Packages
Ign http://us.archive.ubuntu.com edgy-updates/multiverse Packages
Ign http://us.archive.ubuntu.com edgy-updates/main Sources
Ign http://us.archive.ubuntu.com edgy-updates/restricted Sources
Ign http://us.archive.ubuntu.com edgy-updates/universe Sources
Ign http://us.archive.ubuntu.com edgy-updates/multiverse Sources
Err http://us.archive.ubuntu.com edgy/main Packages
  404 Not Found [IP: 146.137.96.7 80]
Err http://us.archive.ubuntu.com edgy/restricted Packages
  404 Not Found [IP: 146.137.96.7 80]
Err http://us.archive.ubuntu.com edgy/universe Packages
  404 Not Found [IP: 146.137.96.7 80]
Err http://us.archive.ubuntu.com edgy/multiverse Packages
  404 Not Found [IP: 146.137.96.7 80]
Err http://us.archive.ubuntu.com edgy/main Sources
  404 Not Found [IP: 146.137.96.7 80]
Err http://us.archive.ubuntu.com edgy/restricted Sources
  404 Not Found [IP: 146.137.96.7 80]
Err http://us.archive.ubuntu.com edgy/universe Sources
  404 Not Found [IP: 146.137.96.7 80]
Err http://us.archive.ubuntu.com edgy/multiverse Sources
  404 Not Found [IP: 146.137.96.7 80]
Err http://us.archive.ubuntu.com edgy-updates/main Packages
  404 Not Found [IP: 146.137.96.7 80]
Err http://us.archive.ubuntu.com edgy-updates/restricted Packages
  404 Not Found [IP: 146.137.96.7 80]
Err http://us.archive.ubuntu.com edgy-updates/universe Packages
  404 Not Found [IP: 146.137.96.7 80]
Err http://us.archive.ubuntu.com edgy-updates/multiverse Packages
  404 Not Found [IP: 146.137.96.7 80]
Err http://us.archive.ubuntu.com edgy-updates/main Sources
  404 Not Found [IP: 146.137.96.7 80]
Err http://us.archive.ubuntu.com edgy-updates/restricted Sources
  404 Not Found [IP: 146.137.96.7 80]
Err http://us.archive.ubuntu.com edgy-updates/universe Sources
  404 Not Found [IP: 146.137.96.7 80]
Err http://us.archive.ubuntu.com edgy-updates/multiverse Sources
  404 Not Found [IP: 146.137.96.7 80]
Fetched 3B in 2m46s (0B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz  404 Not Found [IP: 146.137.96.7 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz  404 Not Found [IP: 146.137.96.7 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz  404 Not Found [IP: 146.137.96.7 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 146.137.96.7 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz  404 Not Found [IP: 146.137.96.7 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz  404 Not Found [IP: 146.137.96.7 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz  404 Not Found [IP: 146.137.96.7 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz  404 Not Found [IP: 146.137.96.7 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz  404 Not Found [IP: 146.137.96.7 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz  404 Not Found [IP: 146.137.96.7 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz  404 Not Found [IP: 146.137.96.7 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 146.137.96.7 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz  404 Not Found [IP: 146.137.96.7 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz  404 Not Found [IP: 146.137.96.7 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/source/Sources.gz  404 Not Found [IP: 146.137.96.7 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/source/Sources.gz  404 Not Found [IP: 146.137.96.7 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

anyone else experiencing the same problem?  perhaps the server is just down...

---

### Post by wilso027 on 2006-12-03
It was down for about 3 hours. Try it again it is up now.

Allan

---

