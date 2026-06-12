---
title: "Epson V39 scanner install errors"
date: 2016-01-29
forum: General Help
---

### Post by paulkruger on 2016-01-29
I purchased an Epson scanner because they had a linux driver.

There are errors on the installation and I could use some help. The text from Terminal is pasted below.

Any help appreciated. :p

======================== TERMINAL ===============


[email]root@Paul-Ubuntu:/home/paul/Downloads/EPSON/iscan-gt-s650-bundle-1.0.0.x86.deb[/email]# ./install.sh
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy InRelease                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates InRelease                       
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease [64.4 kB]           
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease [64.4 kB]          
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy Release.gpg                             
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates Release.gpg                     
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main amd64 Packages [689 kB] 
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                   
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [103 kB]         
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [15.9 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe amd64 Packages [334 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [13.0 kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [663 kB]  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                       
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [4,035 B]  
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [15.6 kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [336 kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [33.1 kB]   
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [13.1 kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en [348 kB]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [2,357 B] 
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages [410 kB] 
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en [6,832 B]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en [3,699 B]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en [176 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy Release                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                     
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
  404  Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main amd64 Packages                
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                     
  404  Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted amd64 Packages          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe amd64 Packages            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse amd64 Packages          
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                           
  404  Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
  404  Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages              
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
  404  Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en              
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages [13.0 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en              
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages [123 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en                
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages [4,798 B]
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [384 kB]  
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [12.7 kB]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [123 kB]
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [4,955 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US             
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe amd64 Packages                 
  404  Not Found [IP: 2001:67c:1562::15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse amd64 Packages
  404  Not Found [IP: 2001:67c:1562::15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe i386 Packages
  404  Not Found [IP: 2001:67c:1562::15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse i386 Packages
  404  Not Found [IP: 2001:67c:1562::15 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy/universe Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe amd64 Packages
  404  Not Found [IP: 2001:67c:1562::15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse amd64 Packages
  404  Not Found [IP: 2001:67c:1562::15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe i386 Packages
  404  Not Found [IP: 2001:67c:1562::15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse i386 Packages
  404  Not Found [IP: 2001:67c:1562::15 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) saucy-updates/universe Translation-en
Fetched 3,961 kB in 38s (103 kB/s)
W: Failed to fetch [http://ppa.launchpad.net/michael-astrapi/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/michael-astrapi/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/michael-astrapi/ppa/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/michael-astrapi/ppa/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/robert-ancell/sane-backends/ubuntu/dists/trusty/main/source/Sources](http://ppa.launchpad.net/robert-ancell/sane-backends/ubuntu/dists/trusty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/robert-ancell/sane-backends/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/robert-ancell/sane-backends/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/robert-ancell/sane-backends/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/robert-ancell/sane-backends/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/saucy/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/saucy/universe/binary-amd64/Packages)  404  Not Found [IP: 2001:67c:1562::15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/saucy/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/saucy/multiverse/binary-amd64/Packages)  404  Not Found [IP: 2001:67c:1562::15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/saucy/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/saucy/universe/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1562::15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/saucy/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/saucy/multiverse/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1562::15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/saucy-updates/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/saucy-updates/universe/binary-amd64/Packages)  404  Not Found [IP: 2001:67c:1562::15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/saucy-updates/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/saucy-updates/multiverse/binary-amd64/Packages)  404  Not Found [IP: 2001:67c:1562::15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/saucy-updates/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/saucy-updates/universe/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1562::15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/saucy-updates/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/saucy-updates/multiverse/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1562::15 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
[email]root@Paul-Ubuntu:/home/paul/Downloads/EPSON/iscan-gt-s650-bundle-1.0.0.x86.deb[/email]# ^C
[email]root@Paul-Ubuntu:/home/paul/Downloads/EPSON/iscan-gt-s650-bundle-1.0.0.x86.deb[/email]#

---

