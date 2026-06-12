---
title: "Cannot update my system at all"
date: 2013-01-14
forum: General Help
---

### Post by snakeman21 on 2013-01-14
Hi all... It's been forever since I've posted on here.  I consider myself a very seasoned Ubuntu user, and usually can solve problems myself or with the help of the all-knowing Google.  But I've hit a stone I just can't seem to move.  I've googled the issue, tried several different solutions, but to no avail.  

My problem is that I can't make system updates.  If I use the software updater, I get "Failed to download repository information.  Check your Internet connection." Followed by:  

```
W:Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-amd64/Packages  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-i386/Packages  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-amd64/Packages  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-security/main/binary-amd64/Packages  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-amd64/Packages  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/Release.gpg  Unable to connect to archive.getdeb.net:http:
, W:Failed to fetch http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/Release.gpg  Unable to connect to archive.getdeb.net:http:
, W:Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/games/source/Sources  Unable to connect to archive.getdeb.net:http:
, W:Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/games/binary-amd64/Packages  Unable to connect to archive.getdeb.net:http:
, W:Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/games/binary-i386/Packages  Unable to connect to archive.getdeb.net:http:
, W:Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/games/i18n/Translation-en  Unable to connect to archive.getdeb.net:http:
, W:Failed to fetch http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/games/binary-amd64/Packages  Unable to connect to archive.getdeb.net:http:
, W:Failed to fetch http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/games/binary-i386/Packages  Unable to connect to archive.getdeb.net:http:
, W:Failed to fetch http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/games/i18n/Translation-en  Unable to connect to archive.getdeb.net:http:
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

If I use the terminal, here is the output:

```
sean@Mean-Machine:~$ sudo apt-get update
[sudo] password for sean: 
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal InRelease
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal Release.gpg
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal Release
Err cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal/main amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal/restricted amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal/main Translation-en_US
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal/main Translation-en
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal/restricted Translation-en_US
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal/restricted Translation-en
Ign http://us.archive.ubuntu.com quantal InRelease                             
Ign http://us.archive.ubuntu.com quantal-updates InRelease                     
Ign http://us.archive.ubuntu.com quantal-security InRelease                    
Hit http://us.archive.ubuntu.com quantal Release.gpg                           
Ign http://archive.canonical.com quantal InRelease                             
Ign http://ppa.launchpad.net quantal InRelease                                 
Ign http://extras.ubuntu.com quantal InRelease                                 
Ign http://archive.ubuntu.com edgy-backports InRelease                         
Hit http://us.archive.ubuntu.com quantal-updates Release.gpg                   
Hit http://us.archive.ubuntu.com quantal-security Release.gpg                  
Hit http://us.archive.ubuntu.com quantal Release                               
Hit http://archive.canonical.com quantal Release.gpg                           
Hit http://ppa.launchpad.net quantal Release.gpg                               
Hit http://extras.ubuntu.com quantal Release.gpg                               
Ign http://archive.ubuntu.com edgy-updates InRelease                           
Hit http://us.archive.ubuntu.com quantal-updates Release                       
Hit http://us.archive.ubuntu.com quantal-security Release                      
Hit http://us.archive.ubuntu.com quantal/main Sources                          
Hit http://archive.canonical.com quantal Release                               
Hit http://ppa.launchpad.net quantal Release                                   
Hit http://extras.ubuntu.com quantal Release                                   
Ign http://archive.ubuntu.com edgy-security InRelease                          
Hit http://us.archive.ubuntu.com quantal/restricted Sources                    
Ign http://archive.ubuntu.com edgy InRelease                                   
Hit http://archive.canonical.com quantal/partner Sources                       
Hit http://ppa.launchpad.net quantal/main Sources                              
Hit http://extras.ubuntu.com quantal/main Sources                              
Hit http://us.archive.ubuntu.com quantal/universe Sources                      
Hit http://us.archive.ubuntu.com quantal/multiverse Sources                    
Ign http://archive.ubuntu.com edgy-backports Release.gpg                       
Hit http://archive.canonical.com quantal/partner amd64 Packages                
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Hit http://us.archive.ubuntu.com quantal/main amd64 Packages                   
Hit http://extras.ubuntu.com quantal/main amd64 Packages                       
Hit http://us.archive.ubuntu.com quantal/restricted amd64 Packages             
Ign http://archive.ubuntu.com edgy-updates Release.gpg                         
Hit http://archive.canonical.com quantal/partner i386 Packages                 
Hit http://us.archive.ubuntu.com quantal/universe amd64 Packages               
Hit http://ppa.launchpad.net quantal/main i386 Packages                        
Hit http://extras.ubuntu.com quantal/main i386 Packages                        
Hit http://us.archive.ubuntu.com quantal/multiverse amd64 Packages             
Ign http://archive.ubuntu.com edgy-security Release.gpg                        
Ign http://archive.ubuntu.com edgy Release.gpg                                 
Hit http://us.archive.ubuntu.com quantal/main i386 Packages                    
Hit http://us.archive.ubuntu.com quantal/restricted i386 Packages              
Hit http://us.archive.ubuntu.com quantal/universe i386 Packages                
Ign http://archive.ubuntu.com edgy-backports Release                           
Hit http://us.archive.ubuntu.com quantal/multiverse i386 Packages              
Ign http://archive.ubuntu.com edgy-updates Release                             
Hit http://us.archive.ubuntu.com quantal/main Translation-en                   
Hit http://us.archive.ubuntu.com quantal/multiverse Translation-en             
Ign http://archive.ubuntu.com edgy-security Release                            
Hit http://us.archive.ubuntu.com quantal/restricted Translation-en             
Ign http://archive.ubuntu.com edgy Release                                     
Hit http://us.archive.ubuntu.com quantal/universe Translation-en               
Hit http://us.archive.ubuntu.com quantal-updates/main Sources                  
Hit http://us.archive.ubuntu.com quantal-updates/restricted Sources            
Hit http://us.archive.ubuntu.com quantal-updates/universe Sources              
Hit http://us.archive.ubuntu.com quantal-updates/multiverse Sources            
Ign http://archive.canonical.com quantal/partner Translation-en_US             
Hit http://us.archive.ubuntu.com quantal-updates/main amd64 Packages           
Ign http://ppa.launchpad.net quantal/main Translation-en_US                    
Ign http://archive.canonical.com quantal/partner Translation-en                
Ign http://extras.ubuntu.com quantal/main Translation-en_US                    
Ign http://ppa.launchpad.net quantal/main Translation-en                       
Hit http://us.archive.ubuntu.com quantal-updates/restricted amd64 Packages     
Hit http://us.archive.ubuntu.com quantal-updates/universe amd64 Packages       
Ign http://extras.ubuntu.com quantal/main Translation-en                       
Hit http://us.archive.ubuntu.com quantal-updates/multiverse amd64 Packages     
Hit http://us.archive.ubuntu.com quantal-updates/main i386 Packages            
Hit http://us.archive.ubuntu.com quantal-updates/restricted i386 Packages      
Hit http://us.archive.ubuntu.com quantal-updates/universe i386 Packages        
Hit http://us.archive.ubuntu.com quantal-updates/multiverse i386 Packages      
Hit http://us.archive.ubuntu.com quantal-updates/main Translation-en         
Hit http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en   
Hit http://us.archive.ubuntu.com quantal-updates/restricted Translation-en   
Hit http://us.archive.ubuntu.com quantal-updates/universe Translation-en     
Hit http://us.archive.ubuntu.com quantal-security/main Sources               
Hit http://us.archive.ubuntu.com quantal-security/restricted Sources         
Hit http://us.archive.ubuntu.com quantal-security/universe Sources           
Hit http://us.archive.ubuntu.com quantal-security/multiverse Sources         
Hit http://us.archive.ubuntu.com quantal-security/main amd64 Packages          
Hit http://us.archive.ubuntu.com quantal-security/restricted amd64 Packages    
Hit http://us.archive.ubuntu.com quantal-security/universe amd64 Packages      
Hit http://us.archive.ubuntu.com quantal-security/multiverse amd64 Packages    
Hit http://us.archive.ubuntu.com quantal-security/main i386 Packages           
Hit http://us.archive.ubuntu.com quantal-security/restricted i386 Packages   
Hit http://us.archive.ubuntu.com quantal-security/universe i386 Packages       
Hit http://us.archive.ubuntu.com quantal-security/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com quantal-security/main Translation-en          
Hit http://us.archive.ubuntu.com quantal-security/multiverse Translation-en    
Hit http://us.archive.ubuntu.com quantal-security/restricted Translation-en  
Hit http://us.archive.ubuntu.com quantal-security/universe Translation-en      
Ign http://us.archive.ubuntu.com quantal/main Translation-en_US                
Ign http://us.archive.ubuntu.com quantal/multiverse Translation-en_US          
Ign http://us.archive.ubuntu.com quantal/restricted Translation-en_US        
Ign http://us.archive.ubuntu.com quantal/universe Translation-en_US          
Ign http://us.archive.ubuntu.com quantal-updates/main Translation-en_US      
Ign http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/universe Translation-en_US    
Ign http://us.archive.ubuntu.com quantal-security/main Translation-en_US       
Ign http://us.archive.ubuntu.com quantal-security/multiverse Translation-en_US 
Ign http://us.archive.ubuntu.com quantal-security/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com quantal-security/universe Translation-en_US   
Err http://archive.ubuntu.com edgy-backports/main amd64 Packages               
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com edgy-backports/restricted amd64 Packages       
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com edgy-backports/universe amd64 Packages         
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com edgy-backports/multiverse amd64 Packages       
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com edgy-backports/main i386 Packages              
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com edgy-backports/restricted i386 Packages
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com edgy-backports/universe i386 Packages          
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com edgy-backports/multiverse i386 Packages        
  404  Not Found [IP: 91.189.92.202 80]
Ign http://archive.ubuntu.com edgy-backports/main Translation-en_US          
Ign http://archive.ubuntu.com edgy-backports/main Translation-en
Ign http://archive.ubuntu.com edgy-backports/multiverse Translation-en_US
Ign http://archive.ubuntu.com edgy-backports/multiverse Translation-en       
Ign http://archive.ubuntu.com edgy-backports/restricted Translation-en_US    
Ign http://archive.ubuntu.com edgy-backports/restricted Translation-en       
Ign http://archive.ubuntu.com edgy-backports/universe Translation-en_US      
Ign http://archive.ubuntu.com edgy-backports/universe Translation-en         
Err http://archive.ubuntu.com edgy-updates/main amd64 Packages               
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com edgy-updates/restricted amd64 Packages         
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com edgy-updates/universe amd64 Packages           
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com edgy-updates/multiverse amd64 Packages         
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com edgy-updates/main i386 Packages                
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com edgy-updates/restricted i386 Packages          
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com edgy-updates/universe i386 Packages
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com edgy-updates/multiverse i386 Packages          
  404  Not Found [IP: 91.189.92.202 80]
Ign http://archive.ubuntu.com edgy-updates/main Translation-en_US            
Ign http://archive.ubuntu.com edgy-updates/main Translation-en               
Ign http://archive.ubuntu.com edgy-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com edgy-updates/multiverse Translation-en
Ign http://archive.ubuntu.com edgy-updates/restricted Translation-en_US      
Ign http://archive.ubuntu.com edgy-updates/restricted Translation-en         
Ign http://archive.ubuntu.com edgy-updates/universe Translation-en_US        
Ign http://archive.ubuntu.com edgy-updates/universe Translation-en           
Err http://archive.ubuntu.com edgy-security/main amd64 Packages              
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com edgy-security/restricted amd64 Packages
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com edgy-security/universe amd64 Packages          
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com edgy-security/multiverse amd64 Packages          
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com edgy-security/main i386 Packages                 
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com edgy-security/restricted i386 Packages         
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com edgy-security/universe i386 Packages           
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com edgy-security/multiverse i386 Packages         
  404  Not Found [IP: 91.189.92.202 80]
Ign http://archive.ubuntu.com edgy-security/main Translation-en_US
Ign http://archive.ubuntu.com edgy-security/main Translation-en
Ign http://archive.ubuntu.com edgy-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com edgy-security/multiverse Translation-en
Ign http://archive.ubuntu.com edgy-security/restricted Translation-en_US
Ign http://archive.ubuntu.com edgy-security/restricted Translation-en
Ign http://archive.ubuntu.com edgy-security/universe Translation-en_US       
Ign http://archive.ubuntu.com edgy-security/universe Translation-en          
Err http://archive.ubuntu.com edgy/main amd64 Packages 
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com edgy/restricted amd64 Packages
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com edgy/universe amd64 Packages                   
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com edgy/multiverse amd64 Packages                 
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com edgy/main i386 Packages  
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com edgy/restricted i386 Packages
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com edgy/universe i386 Packages
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com edgy/multiverse i386 Packages                  
  404  Not Found [IP: 91.189.92.202 80]
Ign http://archive.ubuntu.com edgy/main Translation-en_US                    
Ign http://archive.ubuntu.com edgy/main Translation-en                       
Ign http://archive.ubuntu.com edgy/multiverse Translation-en_US              
Ign http://archive.ubuntu.com edgy/multiverse Translation-en
Ign http://archive.ubuntu.com edgy/restricted Translation-en_US              
Ign http://archive.ubuntu.com edgy/restricted Translation-en                 
Ign http://archive.ubuntu.com edgy/universe Translation-en_US                
Ign http://archive.ubuntu.com edgy/universe Translation-en                   
Ign http://archive.getdeb.net precise-getdeb InRelease 
Ign http://archive.getdeb.net quantal-getdeb InRelease 
Err http://archive.getdeb.net precise-getdeb Release.gpg
  Unable to connect to archive.getdeb.net:http:
Err http://archive.getdeb.net quantal-getdeb Release.gpg
  Unable to connect to archive.getdeb.net:http:
Ign http://archive.getdeb.net precise-getdeb Release
Ign http://archive.getdeb.net quantal-getdeb Release
Err http://archive.getdeb.net precise-getdeb/games Sources
  Unable to connect to archive.getdeb.net:http:
Err http://archive.getdeb.net precise-getdeb/games amd64 Packages
  Unable to connect to archive.getdeb.net:http:
Err http://archive.getdeb.net precise-getdeb/games i386 Packages
  Unable to connect to archive.getdeb.net:http:
Err http://archive.getdeb.net precise-getdeb/games Translation-en_US
  Unable to connect to archive.getdeb.net:http:
Err http://archive.getdeb.net precise-getdeb/games Translation-en
  Unable to connect to archive.getdeb.net:http:
Err http://archive.getdeb.net quantal-getdeb/games amd64 Packages
  Unable to connect to archive.getdeb.net:http:
Err http://archive.getdeb.net quantal-getdeb/games i386 Packages
  Unable to connect to archive.getdeb.net:http:
Err http://archive.getdeb.net quantal-getdeb/games Translation-en_US
  Unable to connect to archive.getdeb.net:http:
Err http://archive.getdeb.net quantal-getdeb/games Translation-en
  Unable to connect to archive.getdeb.net:http:
W: Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-amd64/Packages  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-i386/Packages  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-amd64/Packages  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-security/main/binary-amd64/Packages  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-amd64/Packages  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.92.202 80]

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/Release.gpg  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/Release.gpg  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/games/source/Sources  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/games/binary-amd64/Packages  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/games/binary-i386/Packages  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/games/i18n/Translation-en_US  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/precise-getdeb/games/i18n/Translation-en  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/games/binary-amd64/Packages  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/games/binary-i386/Packages  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/games/i18n/Translation-en_US  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/games/i18n/Translation-en  Unable to connect to archive.getdeb.net:http:

E: Some index files failed to download. They have been ignored, or old ones used instead.
sean@Mean-Machine:~$ 

```

As you can see, it's obviously not just one or two culprit sources that are causing the issue.  It fails to download TONS of stuff.  I've tried changing my server from U.S. to Main and back again.  I've tried fully purging my sources.list file.  One solution after another, all failures.  

This has been going on for quite some time.  Several weeks ago, I installed 12.10.  I ran an update, which worked fine, then I rebooted and went about my business installing all the additional software I wanted.  After that, I ran another update.  Again, no problems.  Shortly after that, I did one more update, which worked fine, but since that day, I haven't been able to run any updates.  Any help would be greatly appreciated!

---

### Post by ibjsb4 on 2013-01-14
Go here and uncheck CDrom.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

You have Edgy in your sources list, need to remove them.

gksudo edit /etc/apt/sources.list

Then update

---

### Post by ibjsb4 on 2013-01-14
Also take a look at sources.list.save and make sure Edgy does not show up there.

AND getdeb has been down for a long time.  Don't know when it will be back up so for now just comment (#) it out in your sources list or sources list.d.  You could also just uncheck it.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

---

### Post by claracc on 2013-01-14
All I can say is that your sources.list file is a mess.

If you are running ubuntu 12.10 as I suppossed, you have to remove all ppas concerning precise pangolin or edgy. Also you remove repositories in cdrom.

I think the best way to start is disabling all ppas in other software in software sources and enabling only software from canonical (main), universe, restricted and multiverse in the ubuntu software tab. Try to update.

Then go enabling ppas (but only that corresponding to your operating system 12.10) one by one and try to update each time.

---

### Post by SlugSlug on 2013-01-14
> **claracc said:**
> All I can say is that your sources.list file is a mess.



Agreed!

I'd start a fresh

Link to generate 
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by snakeman21 on 2013-01-14
> **ibjsb4 said:**
> Go here and uncheck CDrom.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

You have Edgy in your sources list, need to remove them.

gksudo edit /etc/apt/sources.list

Then update

> **ibjsb4 said:**
> Also take a look at sources.list.save and make sure Edgy does not show up there.

AND getdeb has been down for a long time.  Don't know when it will be back up so for now just comment (#) it out in your sources list or sources list.d.  You could also just uncheck it.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

[IMG]http://i0.kym-cdn.com/photos/images/newsfeed/000/011/296/success_baby.jpg?1251168454[/IMG]

Thank you so much, this was the issue.  

I'd noticed edgy showing up in my sources, but I didn't think they were causing the issue because A.) I have had sources from different distros before and they've never caused an issue, and B.) most of the failures it was reporting were for Quantal anyways.  But, I commented out all the getdeb entries for now (wasn't aware that it was down) and deleted all the edgy entries and unchecked cdrom, and lo and behold, a command of "sudo apt-get update" FINALLY yielded proper results.  Thanks again!

---

### Post by ibjsb4 on 2013-01-14
The pic says it all :) welcome

---

