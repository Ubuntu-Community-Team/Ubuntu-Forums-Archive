---
title: "Apt-Get Update Issue [Resolved]"
date: 2006-11-20
forum: General Help
---

### Post by Arkitekt on 2006-11-20
whenever i use 'sudo apt-get update' I get this output

```

jboyd@jboyd-desktop:~$ sudo apt-get update
Get:1 http://ca.archive.ubuntu.com edgy Release.gpg [191B]
Ign http://ca.archive.ubuntu.com edgy/main Translation-en_US                   
Ign http://ca.archive.ubuntu.com edgy/restricted Translation-en_US             
Get:2 http://security.ubuntu.com edgy-security Release.gpg [191B]              
Ign http://security.ubuntu.com edgy-security/main Translation-en_US            
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US      
Ign http://ca.archive.ubuntu.com edgy/universe Translation-en_US               
Ign http://ca.archive.ubuntu.com edgy/multiverse Translation-en_US             
Ign http://ca.archive.ubuntu.com edgy/universe Translation-en_US               
Get:3 http://ca.archive.ubuntu.com edgy-updates Release.gpg [189B]             
Ign http://ca.archive.ubuntu.com edgy-updates/universe Translation-en_US       
Ign http://packages.freecontrib.org edgy Release.gpg                           
Hit http://ca.archive.ubuntu.com edgy Release                                  
Hit http://ca.archive.ubuntu.com edgy-updates Release                          
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US      
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US        
Hit http://security.ubuntu.com edgy-security Release                           
Ign http://packages.freecontrib.org edgy/free Translation-en_US                
Ign http://packages.freecontrib.org edgy/non-free Translation-en_US
Ign http://packages.freecontrib.org edgy Release                               
Hit http://ca.archive.ubuntu.com edgy/main Packages                            
Ign http://packages.freecontrib.org edgy/free Packages                         
Hit http://security.ubuntu.com edgy-security/main Packages                     
Hit http://ca.archive.ubuntu.com edgy/restricted Packages                      
Hit http://ca.archive.ubuntu.com edgy/universe Packages                        
Hit http://ca.archive.ubuntu.com edgy/multiverse Packages                      
Hit http://ca.archive.ubuntu.com edgy/restricted Sources                       
Hit http://ca.archive.ubuntu.com edgy/main Sources                             
Hit http://ca.archive.ubuntu.com edgy/multiverse Sources                       
Hit http://ca.archive.ubuntu.com edgy/universe Sources                         
Hit http://ca.archive.ubuntu.com edgy/universe Packages                        
Hit http://ca.archive.ubuntu.com edgy-updates/restricted Sources               
Hit http://ca.archive.ubuntu.com edgy-updates/main Sources                     
Ign http://packages.freecontrib.org edgy/non-free Packages                     
Hit http://security.ubuntu.com edgy-security/restricted Packages               
Hit http://security.ubuntu.com edgy-security/multiverse Packages               
Hit http://security.ubuntu.com edgy-security/restricted Sources                
Hit http://ca.archive.ubuntu.com edgy-updates/multiverse Sources               
Hit http://ca.archive.ubuntu.com edgy-updates/universe Sources                 
Hit http://ca.archive.ubuntu.com edgy-updates/universe Packages                
Err http://packages.freecontrib.org edgy/free Packages                         
  404 Not Found
Hit http://security.ubuntu.com edgy-security/main Sources                      
Hit http://security.ubuntu.com edgy-security/multiverse Sources 
Hit http://security.ubuntu.com edgy-security/universe Sources   
Hit http://security.ubuntu.com edgy-security/universe Packages  
Err http://packages.freecontrib.org edgy/non-free Packages      
  404 Not Found
Get:4 http://easyubuntu.cafuego.net main Release.gpg [191B]     
Ign http://easyubuntu.cafuego.net main/easyubuntu Translation-en_US
Hit http://easyubuntu.cafuego.net main Release
Hit http://easyubuntu.cafuego.net main/easyubuntu Packages
Fetched 4B in 2s (2B/s)
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/edgy/free/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/edgy/non-free/binary-i386/Packages.gz  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


```

any ideas how to get this working again.

would this have anything to do with the removal of ubuntu-desktio package?

---

### Post by aysiu on 2006-11-20
No, the freecontrib repositories are probably down.

```
sudo nano -B /etc/apt/sources.list
``` Delete (Control-K) the [http://packages.freecontrib.com](http://packages.freecontrib.com) lines, then save (Control-X, Y, Enter and ```
sudo aptitude update
```

---

### Post by Arkitekt on 2006-11-20
thanx, appreciate it alot :D

---

