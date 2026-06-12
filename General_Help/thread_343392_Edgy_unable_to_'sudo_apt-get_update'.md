---
title: "Edgy: unable to 'sudo apt-get update'"
date: 2007-01-21
forum: General Help
---

### Post by kpkeerthi on 2007-01-21
If I run sudo aptitude update... egdy is not downloading any package info.. I'm not able to install any packages too...

```

$:> sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
0% [Connecting to archive.ubuntu.com (1.0.0.0)]  [Connecting to security.ubuntu.com (1.0.0.0)]

```

I tried type [http://archive.ubuntu.com](http://archive.ubuntu.com) in firefox, I get no response. Is the repo down now?

---

### Post by kpkeerthi on 2007-01-21
Can someone please confirm if [http://archive.ubuntu.com](http://archive.ubuntu.com) opens in firefox or is it just me?

---

### Post by dexter on 2007-01-21
> **kpkeerthi said:**
> 
0% [Connecting to archive.ubuntu.com (1.0.0.0)]


Seems like your computer resolves archive.ubuntu.com to ip address 1.0.0.0, which is incorrect (it's 195.248.90.38 in Belgium). Are you able to surf the internet ?

---

### Post by kpkeerthi on 2007-01-21
Yes. I'm able to surf. Seems to be a different problem now... what the...
```

sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Ign http://archive.ubuntu.com edgy Release.gpg                                  
Ign http://archive.ubuntu.com edgy/main Translation-en_US                       
Ign http://archive.ubuntu.com edgy/restricted Translation-en_US                 
Ign http://security.ubuntu.com edgy-security Release.gpg                        
Ign http://security.ubuntu.com edgy-security/main Translation-en_US             
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US       
Ign http://medibuntu.sos-sts.com edgy Release.gpg                               
Ign http://medibuntu.sos-sts.com edgy/free Translation-en_US                    
Ign http://medibuntu.sos-sts.com edgy/non-free Translation-en_US                
Ign http://archive.canonical.com edgy-commercial Release.gpg                    
Ign http://archive.canonical.com edgy-commercial/main Translation-en_US         
Ign http://nvidia.limitless.lupine.me.uk edgy Release.gpg                       
Ign http://nvidia.limitless.lupine.me.uk edgy/stable Translation-en_US          
Ign http://ubuntu.beryl-project.org edgy Release.gpg                            
Ign http://ubuntu.beryl-project.org edgy/main Translation-en_US                 
Get:1 http://malteo.homelinux.net edgy-malteo Release.gpg [189B]                
Ign http://malteo.homelinux.net edgy-malteo/all Translation-en_US               
Ign http://archive.ubuntu.com edgy/universe Translation-en_US                   
Ign http://archive.ubuntu.com edgy/multiverse Translation-en_US                 
Ign http://archive.ubuntu.com edgy-proposed Release.gpg                         
Ign http://archive.ubuntu.com edgy-proposed/main Translation-en_US              
Ign http://archive.ubuntu.com edgy-proposed/restricted Translation-en_US        
Ign http://archive.ubuntu.com edgy-proposed/universe Translation-en_US          
Ign http://archive.ubuntu.com edgy-proposed/multiverse Translation-en_US        
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US         
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US       
Ign http://security.ubuntu.com edgy-security Release                            
Ign http://archive.ubuntu.com edgy-updates Release.gpg                          
Ign http://medibuntu.sos-sts.com edgy Release                                   
Ign http://archive.canonical.com edgy-commercial Release                        
Ign http://nvidia.limitless.lupine.me.uk edgy Release                           
Ign http://ubuntu.beryl-project.org edgy Release                                
Hit http://malteo.homelinux.net edgy-malteo Release                             
Ign http://archive.ubuntu.com edgy-updates/main Translation-en_US               
Ign http://archive.ubuntu.com edgy-updates/restricted Translation-en_US         
Ign http://security.ubuntu.com edgy-security/main Packages                      
Ign http://archive.ubuntu.com edgy-updates/universe Translation-en_US           
Ign http://archive.ubuntu.com edgy-updates/multiverse Translation-en_US         
Ign http://archive.ubuntu.com edgy-backports Release.gpg                        
Ign http://archive.ubuntu.com edgy-backports/main Translation-en_US             
Ign http://medibuntu.sos-sts.com edgy/free Packages                             
Ign http://archive.canonical.com edgy-commercial/main Packages                  
Ign http://nvidia.limitless.lupine.me.uk edgy/stable Packages                   
Ign http://ubuntu.beryl-project.org edgy/main Packages                          
Hit http://malteo.homelinux.net edgy-malteo/all Packages                        
Ign http://archive.ubuntu.com edgy-backports/restricted Translation-en_US       
Ign http://archive.ubuntu.com edgy-backports/universe Translation-en_US         
Ign http://archive.ubuntu.com edgy-backports/multiverse Translation-en_US       
Ign http://security.ubuntu.com edgy-security/restricted Packages                
Ign http://security.ubuntu.com edgy-security/universe Packages                  
Ign http://security.ubuntu.com edgy-security/multiverse Packages                
Ign http://security.ubuntu.com edgy-security/main Sources                       
Ign http://archive.ubuntu.com edgy Release                                      
Ign http://archive.ubuntu.com edgy-proposed Release                             
Ign http://archive.ubuntu.com edgy-updates Release                              
Ign http://medibuntu.sos-sts.com edgy/non-free Packages                         
Ign http://medibuntu.sos-sts.com edgy/free Sources                              
Ign http://medibuntu.sos-sts.com edgy/non-free Sources                          
Err http://archive.canonical.com edgy-commercial/main Packages                  
  404 Not Found
Err http://nvidia.limitless.lupine.me.uk edgy/stable Packages                   
  404 Not Found
Err http://ubuntu.beryl-project.org edgy/main Packages                          
  404 Not Found
Hit http://malteo.homelinux.net edgy-malteo/all Sources                         
Ign http://security.ubuntu.com edgy-security/restricted Sources                 
Ign http://security.ubuntu.com edgy-security/universe Sources        
Ign http://security.ubuntu.com edgy-security/multiverse Sources      
Err http://security.ubuntu.com edgy-security/main Packages           
  404 Not Found
Ign http://archive.ubuntu.com edgy-backports Release                 
Ign http://archive.ubuntu.com edgy/main Packages                     
Ign http://archive.ubuntu.com edgy/restricted Packages               
Ign http://archive.ubuntu.com edgy/universe Packages                 
Ign http://archive.ubuntu.com edgy/multiverse Packages               
Ign http://archive.ubuntu.com edgy/main Sources                      
Ign http://archive.ubuntu.com edgy/restricted Sources                
Err http://medibuntu.sos-sts.com edgy/free Packages                  
  404 Not Found
Ign http://archive.ubuntu.com edgy/universe Sources                  
Ign http://archive.ubuntu.com edgy/multiverse Sources                
Ign http://archive.ubuntu.com edgy-proposed/main Packages            
Ign http://archive.ubuntu.com edgy-proposed/restricted Packages      
Ign http://archive.ubuntu.com edgy-proposed/universe Packages        
Ign http://archive.ubuntu.com edgy-proposed/multiverse Packages      
Ign http://archive.ubuntu.com edgy-updates/main Packages             
Ign http://archive.ubuntu.com edgy-updates/restricted Packages       
Err http://medibuntu.sos-sts.com edgy/non-free Packages              
  404 Not Found
Err http://medibuntu.sos-sts.com edgy/free Sources
  404 Not Found
Ign http://archive.ubuntu.com edgy-updates/universe Packages
Err http://security.ubuntu.com edgy-security/restricted Packages
  404 Not Found
Err http://security.ubuntu.com edgy-security/universe Packages
  404 Not Found
Err http://security.ubuntu.com edgy-security/multiverse Packages
  404 Not Found
Err http://security.ubuntu.com edgy-security/main Sources
  404 Not Found
Err http://security.ubuntu.com edgy-security/restricted Sources
  404 Not Found
Err http://security.ubuntu.com edgy-security/universe Sources
  404 Not Found
Err http://security.ubuntu.com edgy-security/multiverse Sources
  404 Not Found
Ign http://archive.ubuntu.com edgy-updates/multiverse Packages
Ign http://archive.ubuntu.com edgy-updates/main Sources
Ign http://archive.ubuntu.com edgy-updates/restricted Sources
Ign http://archive.ubuntu.com edgy-updates/universe Sources
Ign http://archive.ubuntu.com edgy-updates/multiverse Sources
Ign http://archive.ubuntu.com edgy-backports/main Packages
Ign http://archive.ubuntu.com edgy-backports/restricted Packages
Err http://medibuntu.sos-sts.com edgy/non-free Sources
  404 Not Found
Ign http://archive.ubuntu.com edgy-backports/universe Packages
Ign http://archive.ubuntu.com edgy-backports/multiverse Packages
Ign http://archive.ubuntu.com edgy-backports/main Sources
Ign http://archive.ubuntu.com edgy-backports/restricted Sources
Ign http://archive.ubuntu.com edgy-backports/universe Sources
Ign http://archive.ubuntu.com edgy-backports/multiverse Sources
Err http://archive.ubuntu.com edgy/main Packages
  404 Not Found
Err http://archive.ubuntu.com edgy/restricted Packages
  404 Not Found
Err http://archive.ubuntu.com edgy/universe Packages
  404 Not Found
Err http://archive.ubuntu.com edgy/multiverse Packages
  404 Not Found
Err http://archive.ubuntu.com edgy/main Sources
  404 Not Found
Err http://archive.ubuntu.com edgy/restricted Sources
  404 Not Found
Err http://archive.ubuntu.com edgy/universe Sources
  404 Not Found
Err http://archive.ubuntu.com edgy/multiverse Sources
  404 Not Found
Err http://archive.ubuntu.com edgy-proposed/main Packages
  404 Not Found
Err http://archive.ubuntu.com edgy-proposed/restricted Packages
  404 Not Found
Err http://archive.ubuntu.com edgy-proposed/universe Packages
  404 Not Found
Err http://archive.ubuntu.com edgy-proposed/multiverse Packages
  404 Not Found
Err http://archive.ubuntu.com edgy-updates/main Packages
  404 Not Found
Err http://archive.ubuntu.com edgy-updates/restricted Packages
  404 Not Found
Err http://archive.ubuntu.com edgy-updates/universe Packages
  404 Not Found
Err http://archive.ubuntu.com edgy-updates/multiverse Packages
  404 Not Found
Err http://archive.ubuntu.com edgy-updates/main Sources
  404 Not Found
Err http://archive.ubuntu.com edgy-updates/restricted Sources
  404 Not Found
Err http://archive.ubuntu.com edgy-updates/universe Sources
  404 Not Found
Err http://archive.ubuntu.com edgy-updates/multiverse Sources
  404 Not Found
Err http://archive.ubuntu.com edgy-backports/main Packages
  404 Not Found
Err http://archive.ubuntu.com edgy-backports/restricted Packages
  404 Not Found
Err http://archive.ubuntu.com edgy-backports/universe Packages
  404 Not Found
Err http://archive.ubuntu.com edgy-backports/multiverse Packages
  404 Not Found
Err http://archive.ubuntu.com edgy-backports/main Sources
  404 Not Found
Err http://archive.ubuntu.com edgy-backports/restricted Sources
  404 Not Found
Err http://archive.ubuntu.com edgy-backports/universe Sources
  404 Not Found
Err http://archive.ubuntu.com edgy-backports/multiverse Sources
  404 Not Found
Fetched 1B in 4s (0B/s)  
Reading package lists... Done


```

---

### Post by kpkeerthi on 2007-01-22
I don't understand why the f%^&  the IP resolves to a crazy 1.0.0.0. I found the solution here [http://www.mepis.org/node/10330#comment-36642](http://www.mepis.org/node/10330#comment-36642) 

Thanks a million to the mepis user.

---

### Post by waterspider on 2007-08-20
sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory
iceman@braveheart:~$

---

### Post by mckooiker on 2007-09-29
Usually I get this message if I am running the synaptic manager or any other program to install/update software... If this is the case, just close these programs down and retry, otherwise forget what I just said.

---

