---
title: "Error message: 'Requires installation of untrusted packages' in Ubuntu 10.10"
date: 2013-03-14
forum: General Help
---

### Post by johnny907 on 2013-03-14
cannot install anything in software center and get 'Requires installation of untrusted packages' message, also when I try to update in terminal I get the 'failed to fetch....etc' message.  Here is what it looks like:

```
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US       
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                     
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) maverick/main Translation-en   
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) maverick/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
Get:2 [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg [198B]                 
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Get:3 [http://deb.opera.com](http://deb.opera.com) stable Release.gpg [189B]                           
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-en                 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                       
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                     
Ign [http://ppa.launchpad.net/elementaryart/ppa/ubuntu/](http://ppa.launchpad.net/elementaryart/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/elementaryart/ppa/ubuntu/](http://ppa.launchpad.net/elementaryart/ppa/ubuntu/) maverick/main Translation-en_US
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                     
Ign [http://ppa.launchpad.net/hydr0g3n/qbittorrent-unstable/ubuntu/](http://ppa.launchpad.net/hydr0g3n/qbittorrent-unstable/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/hydr0g3n/qbittorrent-unstable/ubuntu/](http://ppa.launchpad.net/hydr0g3n/qbittorrent-unstable/ubuntu/) maverick/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Ign [http://ppa.launchpad.net/leo.robol/tastebook/ubuntu/](http://ppa.launchpad.net/leo.robol/tastebook/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/leo.robol/tastebook/ubuntu/](http://ppa.launchpad.net/leo.robol/tastebook/ubuntu/) maverick/main Translation-en_US
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-en_US              
Get:6 [http://deb.opera.com](http://deb.opera.com) stable Release.gpg [189B]                           
Ign [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) stable/non-free Translation-en            
Ign [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) stable/non-free Translation-en_US         
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources/DiffIndex        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources/DiffIndex               
Ign [http://ppa.launchpad.net/transmissionbt/ppa/ubuntu/](http://ppa.launchpad.net/transmissionbt/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/transmissionbt/ppa/ubuntu/](http://ppa.launchpad.net/transmissionbt/ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources/DiffIndex         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources/DiffIndex           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main amd64 Packages/DiffIndex        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted amd64 Packages/DiffIndex  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse amd64 Packages/DiffIndex  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe amd64 Packages/DiffIndex    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources/DiffIndex  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources/DiffIndex    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main amd64 Packages/DiffIndex 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main amd64 Packages                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted amd64 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse amd64 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe amd64 Packages/DiffIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources/DiffIndex       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources/DiffIndex 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources/DiffIndex   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main amd64 Packages/DiffIndex
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free amd64 Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner amd64 Packages               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted amd64 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse amd64 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe amd64 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main amd64 Packages                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted amd64 Packages            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse amd64 Packages            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe amd64 Packages              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources                 
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free amd64 Packages                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main amd64 Packages          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted amd64 Packages    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main amd64 Packages           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted amd64 Packages     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse amd64 Packages     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main amd64 Packages                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse amd64 Packages    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe amd64 Packages      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main amd64 Packages                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free amd64 Packages                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe amd64 Packages       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted amd64 Packages            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse amd64 Packages            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe amd64 Packages              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources           
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
  404  Not Found
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main amd64 Packages          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted amd64 Packages    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse amd64 Packages    
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free amd64 Packages                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe amd64 Packages      
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources                         
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources                   
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources                     
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main amd64 Packages                  
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted amd64 Packages            
  404  Not Found [IP: 91.189.91.14 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main amd64 Packages           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted amd64 Packages     
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main amd64 Packages                      
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse amd64 Packages            
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe amd64 Packages              
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources                 
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources           
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources             
  404  Not Found [IP: 91.189.91.14 80]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                      
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main amd64 Packages          
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted amd64 Packages    
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse amd64 Packages    
  404  Not Found [IP: 91.189.91.14 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe amd64 Packages      
  404  Not Found [IP: 91.189.91.14 80]
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free amd64 Packages                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse amd64 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe amd64 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages            
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources        
  404  Not Found [IP: 91.189.92.200 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources  
  404  Not Found [IP: 91.189.92.200 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources    
  404  Not Found [IP: 91.189.92.200 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main amd64 Packages 
  404  Not Found [IP: 91.189.92.200 80]
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free amd64 Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted amd64 Packages
  404  Not Found [IP: 91.189.92.200 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse amd64 Packages
  404  Not Found [IP: 91.189.92.200 80]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe amd64 Packages
  404  Not Found [IP: 91.189.92.200 80]
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages
  404  Not Found
Fetched 1,840B in 3s (602B/s)
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found


W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  404  Not Found


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz)  404  Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  404  Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz)  404  Not Found [IP: 91.189.92.200 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-amd64/Packages.gz)  404  Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-amd64/Packages.gz)  404  Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-amd64/Packages.gz)  404  Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz)  404  Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz)  404  Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-amd64/Packages.gz)  404  Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-amd64/Packages.gz)  404  Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-amd64/Packages.gz)  404  Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-amd64/Packages.gz)  404  Not Found [IP: 91.189.91.14 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.92.200 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz)  404  Not Found [IP: 91.189.92.200 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-amd64/Packages.gz)  404  Not Found [IP: 91.189.92.200 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-amd64/Packages.gz)  404  Not Found [IP: 91.189.92.200 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-amd64/Packages.gz)  404  Not Found [IP: 91.189.92.200 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-amd64/Packages.gz)  404  Not Found [IP: 91.189.92.200 80]


W: Failed to fetch [http://ppa.launchpad.net/leo.robol/tastebook/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/leo.robol/tastebook/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/leo.robol/tastebook/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/leo.robol/tastebook/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  404  Not Found


E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by sanderj on 2013-03-14
Yep ... 10.10 is not supported anymore. See [http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions)

---

