---
title: "Something wrong with my repos?"
date: 2007-07-22
forum: General Help
---

### Post by herbster on 2007-07-22
I wanted to install gparted so I did apt-get install gparted, but it gives me an error. I did sudo apt-get update and I'm getting:

```
bobby:~$ sudo apt-get update
Err http://ca.archive.ubuntu.com feisty Release.gpg
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Err http://ca.archive.ubuntu.com feisty/main Translation-en_CA                        
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Err http://ca.archive.ubuntu.com feisty/restricted Translation-en_CA                  
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Err http://ca.archive.ubuntu.com feisty/universe Translation-en_CA                    
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Err http://ca.archive.ubuntu.com feisty/multiverse Translation-en_CA                  
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Err http://ca.archive.ubuntu.com feisty-updates Release.gpg                           
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Err http://ca.archive.ubuntu.com feisty-updates/main Translation-en_CA                
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Err http://ca.archive.ubuntu.com feisty-updates/restricted Translation-en_CA          
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Ign http://ca.archive.ubuntu.com feisty Release                                       
Ign http://ca.archive.ubuntu.com feisty-updates Release                               
Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]                   
Ign http://security.ubuntu.com feisty-security/main Translation-en_CA                 
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_CA           
Ign http://ca.archive.ubuntu.com feisty/main Packages                                 
Ign http://ca.archive.ubuntu.com feisty/restricted Packages                           
Ign http://ca.archive.ubuntu.com feisty/main Sources                                  
Ign http://ca.archive.ubuntu.com feisty/restricted Sources                            
Ign http://security.ubuntu.com feisty-security/universe Translation-en_CA             
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_CA           
Hit http://security.ubuntu.com feisty-security Release                                
Ign http://ca.archive.ubuntu.com feisty/universe Packages                             
Ign http://ca.archive.ubuntu.com feisty/universe Sources                              
Ign http://ca.archive.ubuntu.com feisty/multiverse Packages                           
Ign http://ca.archive.ubuntu.com feisty/multiverse Sources                            
Ign http://ca.archive.ubuntu.com feisty-updates/main Packages                         
Ign http://ca.archive.ubuntu.com feisty-updates/restricted Packages                   
Hit http://security.ubuntu.com feisty-security/main Packages                          
Ign http://ca.archive.ubuntu.com feisty-updates/main Sources                          
Ign http://ca.archive.ubuntu.com feisty-updates/restricted Sources                    
Err http://ca.archive.ubuntu.com feisty/main Packages                                 
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Err http://ca.archive.ubuntu.com feisty/restricted Packages                           
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Err http://ca.archive.ubuntu.com feisty/main Sources                                  
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Hit http://security.ubuntu.com feisty-security/restricted Packages                    
Hit http://security.ubuntu.com feisty-security/main Sources                           
Hit http://security.ubuntu.com feisty-security/restricted Sources                     
Err http://ca.archive.ubuntu.com feisty/restricted Sources                            
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Err http://ca.archive.ubuntu.com feisty/universe Packages                             
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Err http://ca.archive.ubuntu.com feisty/universe Sources                              
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Err http://ca.archive.ubuntu.com feisty/multiverse Packages                           
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Err http://ca.archive.ubuntu.com feisty/multiverse Sources                            
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Hit http://security.ubuntu.com feisty-security/universe Packages                      
Hit http://security.ubuntu.com feisty-security/universe Sources                       
Hit http://security.ubuntu.com feisty-security/multiverse Packages                    
Hit http://security.ubuntu.com feisty-security/multiverse Sources                     
Err http://ca.archive.ubuntu.com feisty-updates/main Packages                         
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Err http://ca.archive.ubuntu.com feisty-updates/restricted Packages                   
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Err http://ca.archive.ubuntu.com feisty-updates/main Sources                          
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Err http://ca.archive.ubuntu.com feisty-updates/restricted Sources                    
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Get:2 http://www.claws-mail.org ./ Release.gpg [189B]                                 
Ign http://www.claws-mail.org ./ Translation-en_CA                                    
Hit http://www.claws-mail.org ./ Release                                        
Hit http://www.claws-mail.org ./ Packages                                    
Get:3 http://packages.medibuntu.org feisty Release.gpg [189B]                         
Ign http://packages.medibuntu.org feisty/free Translation-en_CA
Ign http://packages.medibuntu.org feisty/non-free Translation-en_CA
Hit http://packages.medibuntu.org feisty Release
Ign http://packages.medibuntu.org feisty/free Packages
Ign http://packages.medibuntu.org feisty/non-free Packages
Hit http://packages.medibuntu.org feisty/free Packages
Hit http://packages.medibuntu.org feisty/non-free Packages
Fetched 3B in 2m6s (0B/s)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_CA.bz2 Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_CA.bz2 Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_CA.bz2 Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_CA.bz2 Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_CA.bz2 Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_CA.bz2 Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

I do not want to mess with my sources.list or anything. And my internet connection is working 100% fine during all of this.

TIA!

---

### Post by bapoumba on 2007-07-22
[http://ubuntuforums.org/showthread.php?t=506939]("http://ubuntuforums.org/showthread.php?t=506939")
Please try the main servers. Looks like there are some problems with the ca repos.

---

### Post by herbster on 2007-07-22
> **bapoumba said:**
> [http://ubuntuforums.org/showthread.php?t=506939]("http://ubuntuforums.org/showthread.php?t=506939")
Please try the main servers. Looks like there are some problems with the ca repos.

Thank you bapoumba!

---

