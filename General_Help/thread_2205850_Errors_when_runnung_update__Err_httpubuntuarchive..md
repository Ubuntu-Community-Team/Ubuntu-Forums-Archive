---
title: "Errors when runnung update : Err http://ubuntuarchive.eweka.nl oneiric"
date: 2014-02-16
forum: General Help
---

### Post by CarlWalters on 2014-02-16
I'm running 13.10 and have just started seeing the following error messages whenever I try to update using "sudo apt-get update" 
(The errors come right at the end)

Could anyone tell me if these are anything to worry about please.  Many thanks :)

```

carl@carl-Dell-DXC051:~$ sudo apt-get update
Ign http://extras.ubuntu.com oneiric InRelease
Ign http://gb.archive.ubuntu.com oneiric InRelease                                                                                                                                                                                            
Ign http://dl.google.com stable InRelease                                                                                                                                                                                                     
Hit http://extras.ubuntu.com oneiric Release.gpg                                                                                                                                                                                   
Ign http://gb.archive.ubuntu.com oneiric-updates InRelease                                                                                                                                                   
Ign http://ppa.launchpad.net saucy InRelease                                                                                                                                                                 
Hit http://deb.playonlinux.com precise InRelease                                                                                                                                                             
Ign http://gb.archive.ubuntu.com oneiric-backports InRelease                                                                                                                                                 
Ign http://security.ubuntu.com oneiric-security InRelease                                                                                                         
Ign http://ppa.launchpad.net saucy InRelease                                                                                                                      
Ign http://ppa.launchpad.net saucy InRelease                                                                                                                      
Hit http://dl.google.com stable Release.gpg                                                                                                                       
Ign http://archive.canonical.com oneiric InRelease                                                                                                                
Hit http://extras.ubuntu.com oneiric Release                                    
Hit http://gb.archive.ubuntu.com oneiric Release.gpg                            
Hit http://gb.archive.ubuntu.com oneiric-updates Release.gpg                                             
Hit http://archive.canonical.com oneiric Release.gpg                                                                                                                                             
Hit http://ppa.launchpad.net saucy Release.gpg                                                                                                                                                   
Hit http://security.ubuntu.com oneiric-security Release.gpg                                                                                                                                      
Hit http://dl.google.com stable Release                                                                                                                                    
Hit http://gb.archive.ubuntu.com oneiric-backports Release.gpg                                                                                                             
Hit http://ppa.launchpad.net saucy Release.gpg                                                                                                                             
Hit http://archive.canonical.com oneiric Release                                                                                                                           
Hit http://security.ubuntu.com oneiric-security Release                                                                                                                    
Hit http://gb.archive.ubuntu.com oneiric Release                                                                                                     
Hit http://ppa.launchpad.net saucy Release.gpg                                                                                 
Hit http://gb.archive.ubuntu.com oneiric-updates Release                                                                       
Hit http://ppa.launchpad.net saucy Release                                                                                     
Hit http://gb.archive.ubuntu.com oneiric-backports Release                                                                     
Hit http://ppa.launchpad.net saucy Release                                                                                     
Hit http://ppa.launchpad.net saucy Release                                                               
Hit http://deb.playonlinux.com precise/main i386 Packages                                              
Hit http://extras.ubuntu.com oneiric/main Sources                                                                            
Hit http://extras.ubuntu.com oneiric/main i386 Packages                                                                      
Hit http://archive.canonical.com oneiric/partner i386 Packages                                                                                                           
Hit http://dl.google.com stable/main i386 Packages                                                                                                                       
Hit http://security.ubuntu.com oneiric-security/main Sources                                                                                                                                   
Hit http://gb.archive.ubuntu.com oneiric/main Sources                                                                                                                                          
Hit http://gb.archive.ubuntu.com oneiric/restricted Sources                                                                                                                                    
Hit http://security.ubuntu.com oneiric-security/restricted Sources                                                                                                                                                   
Ign http://extras.ubuntu.com oneiric/main Translation-en_GB                                                                                                                                                          
Hit http://gb.archive.ubuntu.com oneiric/universe Sources                                                                                                                                                            
Hit http://security.ubuntu.com oneiric-security/universe Sources                                                                                                                                                     
Ign http://extras.ubuntu.com oneiric/main Translation-en                                                                                                                                                             
Hit http://gb.archive.ubuntu.com oneiric/multiverse Sources                                                                                                                                                          
Hit http://security.ubuntu.com oneiric-security/multiverse Sources                                                                                                                             
Ign http://archive.canonical.com oneiric/partner Translation-en_GB                                                                                                                             
Hit http://gb.archive.ubuntu.com oneiric/main i386 Packages                                                                                                                                    
Ign http://archive.canonical.com oneiric/partner Translation-en                                                                                                                                                      
Hit http://security.ubuntu.com oneiric-security/main i386 Packages                                                                                                                                                   
Hit http://gb.archive.ubuntu.com oneiric/restricted i386 Packages                                                                                                                              
Hit http://ppa.launchpad.net saucy/main i386 Packages                                                                                                                                          
Ign http://deb.playonlinux.com precise/main Translation-en_GB                                                                                                                                  
Hit http://gb.archive.ubuntu.com oneiric/universe i386 Packages                                                                                                          
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages                                                                                                                       
Hit http://gb.archive.ubuntu.com oneiric/multiverse i386 Packages                                                                                                                              
Ign http://deb.playonlinux.com precise/main Translation-en                                                                                                                                     
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages                                                                                                  
Hit http://ppa.launchpad.net saucy/main i386 Packages                                                                                             
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages                                                                          
Hit http://gb.archive.ubuntu.com oneiric/main Translation-en_GB                                                                                   
Hit http://security.ubuntu.com oneiric-security/main Translation-en                                                                               
Hit http://gb.archive.ubuntu.com oneiric/main Translation-en                                                                                      
Hit http://ppa.launchpad.net saucy/main i386 Packages                                                                                             
Hit http://gb.archive.ubuntu.com oneiric/multiverse Translation-en_GB                                                                             
Ign http://dl.google.com stable/main Translation-en_GB                                                                                            
Hit http://gb.archive.ubuntu.com oneiric/multiverse Translation-en                                                                                
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en                                                                         
Hit http://gb.archive.ubuntu.com oneiric/restricted Translation-en_GB                                                                             
Ign http://dl.google.com stable/main Translation-en                                                                                               
Hit http://gb.archive.ubuntu.com oneiric/restricted Translation-en                                                                                
Hit http://gb.archive.ubuntu.com oneiric/universe Translation-en_GB                                                         
Hit http://gb.archive.ubuntu.com oneiric/universe Translation-en                                                            
Hit http://gb.archive.ubuntu.com oneiric-updates/main Sources                                                               
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en                                                   
Hit http://gb.archive.ubuntu.com oneiric-updates/restricted Sources                                                         
Hit http://gb.archive.ubuntu.com oneiric-updates/universe Sources                                                           
Hit http://gb.archive.ubuntu.com oneiric-updates/multiverse Sources                                                         
Hit http://security.ubuntu.com oneiric-security/universe Translation-en                                                     
Hit http://gb.archive.ubuntu.com oneiric-updates/main i386 Packages                                                         
Hit http://gb.archive.ubuntu.com oneiric-updates/restricted i386 Packages                                                   
Hit http://gb.archive.ubuntu.com oneiric-updates/universe i386 Packages                                                     
Hit http://gb.archive.ubuntu.com oneiric-updates/multiverse i386 Packages                                                   
Hit http://gb.archive.ubuntu.com oneiric-updates/main Translation-en                                                        
Ign http://ppa.launchpad.net saucy/main Translation-en_GB                                                                   
Hit http://gb.archive.ubuntu.com oneiric-updates/multiverse Translation-en                                                  
Hit http://gb.archive.ubuntu.com oneiric-updates/restricted Translation-en                                                  
Hit http://gb.archive.ubuntu.com oneiric-updates/universe Translation-en                                                    
Ign http://ppa.launchpad.net saucy/main Translation-en                                                                      
Hit http://gb.archive.ubuntu.com oneiric-backports/main Sources                                                             
Ign http://ppa.launchpad.net saucy/main Translation-en_GB                                                                   
Hit http://gb.archive.ubuntu.com oneiric-backports/restricted Sources                                                       
Ign http://security.ubuntu.com oneiric-security/main Translation-en_GB                                                      
Ign http://ppa.launchpad.net saucy/main Translation-en                                                                      
Ign http://ppa.launchpad.net saucy/main Translation-en_GB                                                                   
Hit http://gb.archive.ubuntu.com oneiric-backports/universe Sources                                                         
Ign http://security.ubuntu.com oneiric-security/multiverse Translation-en_GB                                                
Ign http://ppa.launchpad.net saucy/main Translation-en                                                                      
Hit http://gb.archive.ubuntu.com oneiric-backports/multiverse Sources                                                       
Ign http://security.ubuntu.com oneiric-security/restricted Translation-en_GB                          
Hit http://gb.archive.ubuntu.com oneiric-backports/main i386 Packages                                 
Ign http://security.ubuntu.com oneiric-security/universe Translation-en_GB                            
Hit http://gb.archive.ubuntu.com oneiric-backports/restricted i386 Packages                           
Hit http://gb.archive.ubuntu.com oneiric-backports/universe i386 Packages       
Hit http://gb.archive.ubuntu.com oneiric-backports/multiverse i386 Packages     
Hit http://gb.archive.ubuntu.com oneiric-backports/main Translation-en          
Hit http://gb.archive.ubuntu.com oneiric-backports/multiverse Translation-en    
Hit http://gb.archive.ubuntu.com oneiric-backports/restricted Translation-en    
Hit http://gb.archive.ubuntu.com oneiric-backports/universe Translation-en      
Ign http://gb.archive.ubuntu.com oneiric-updates/main Translation-en_GB         
Ign http://gb.archive.ubuntu.com oneiric-updates/multiverse Translation-en_GB   
Ign http://gb.archive.ubuntu.com oneiric-updates/restricted Translation-en_GB   
Ign http://gb.archive.ubuntu.com oneiric-updates/universe Translation-en_GB     
Ign http://gb.archive.ubuntu.com oneiric-backports/main Translation-en_GB       
Ign http://gb.archive.ubuntu.com oneiric-backports/multiverse Translation-en_GB 
Ign http://gb.archive.ubuntu.com oneiric-backports/restricted Translation-en_GB 
Ign http://gb.archive.ubuntu.com oneiric-backports/universe Translation-en_GB
Err http://ubuntuarchive.eweka.nl oneiric InRelease       
  
Err http://ubuntuarchive.eweka.nl oneiric-updates InRelease
  
Err http://ubuntuarchive.eweka.nl oneiric-security InRelease
  
Err http://ubuntuarchive.eweka.nl oneiric Release.gpg     
  Cannot initiate the connection to ubuntuarchive.eweka.nl:80 (2001:4de0:1:a::2). - connect (101: Network is unreachable) [IP: 2001:4de0:1:a::2 80]
Err http://ubuntuarchive.eweka.nl oneiric-updates Release.gpg
  Cannot initiate the connection to ubuntuarchive.eweka.nl:80 (2001:4de0:1:a::2). - connect (101: Network is unreachable) [IP: 2001:4de0:1:a::2 80]
Err http://ubuntuarchive.eweka.nl oneiric-security Release.gpg
  Cannot initiate the connection to ubuntuarchive.eweka.nl:80 (2001:4de0:1:a::2). - connect (101: Network is unreachable) [IP: 2001:4de0:1:a::2 80]
Reading package lists... Done
W: Failed to fetch http://ubuntuarchive.eweka.nl/ubuntu/dists/oneiric/InRelease  

W: Failed to fetch http://ubuntuarchive.eweka.nl/ubuntu/dists/oneiric-updates/InRelease  

W: Failed to fetch http://ubuntuarchive.eweka.nl/ubuntu/dists/oneiric-security/InRelease  

W: Failed to fetch http://ubuntuarchive.eweka.nl/ubuntu/dists/oneiric/Release.gpg  Cannot initiate the connection to ubuntuarchive.eweka.nl:80 (2001:4de0:1:a::2). - connect (101: Network is unreachable) [IP: 2001:4de0:1:a::2 80]

W: Failed to fetch http://ubuntuarchive.eweka.nl/ubuntu/dists/oneiric-updates/Release.gpg  Cannot initiate the connection to ubuntuarchive.eweka.nl:80 (2001:4de0:1:a::2). - connect (101: Network is unreachable) [IP: 2001:4de0:1:a::2 80]

W: Failed to fetch http://ubuntuarchive.eweka.nl/ubuntu/dists/oneiric-security/Release.gpg  Cannot initiate the connection to ubuntuarchive.eweka.nl:80 (2001:4de0:1:a::2). - connect (101: Network is unreachable) [IP: 2001:4de0:1:a::2 80]

W: Some index files failed to download. They have been ignored, or old ones used instead.



```

---

### Post by jeanjd63 on 2014-02-16
Hello.
This site : **[http://ubuntuarchive.eweka.nl](http://ubuntuarchive.eweka.nl) **seems to not exist.
You can search where is referenced :
[B]sudo  grep  -i  "eweka" /etc/apt/sources.list
sudo  grep  -Hi  "eweka" /etc/apt/sources.list.d/*[/B]

---

### Post by Iowan on 2014-02-16
Oneiric was 11.10 - which went EOL May 9, 2013.

---

### Post by CarlWalters on 2014-02-16
thanks :). The results of those two greps are:

```

carl@carl-Dell-DXC051:~$ sudo grep -i "eweka" /etc/apt/sources.list
deb http://ubuntuarchive.eweka.nl/ubuntu/ oneiric main restricted
deb-src http://ubuntuarchive.eweka.nl/ubuntu/ oneiric main restricted
deb http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates main restricted
deb-src http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates main restricted
deb http://ubuntuarchive.eweka.nl/ubuntu/ oneiric universe
deb-src http://ubuntuarchive.eweka.nl/ubuntu/ oneiric universe
deb http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates universe
deb-src http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates universe
deb http://ubuntuarchive.eweka.nl/ubuntu/ oneiric multiverse
deb-src http://ubuntuarchive.eweka.nl/ubuntu/ oneiric multiverse
deb http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates multiverse
deb-src http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-updates multiverse
deb http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-security main restricted
deb-src http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-security main restricted
deb http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-security universe
deb-src http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-security universe
deb http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-security multiverse
deb-src http://ubuntuarchive.eweka.nl/ubuntu/ oneiric-security multiverse

```

```

carl@carl-Dell-DXC051:~$ sudo grep -Hi "eweka" /etc/apt/sources.list.d/*
carl@carl-Dell-DXC051:~$ 

```

Can I just edit those lines out of /etc/apt/sources.list?

---

### Post by jeanjd63 on 2014-02-16
I think you have to change you server of update

---

