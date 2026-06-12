---
title: "Failed to download repository information"
date: 2014-06-12
forum: General Help
---

### Post by SUPERFITTER on 2014-06-12
I have the same problem, [SIZE=2]Failed to download repository information[/SIZE].  I'm running Ubuntu 12.04.  How do I correct this problem? How do I reinstall the ppa?

Thank you

```
dennis@dennis1:~$ sudo apt-get update
[sudo] password for dennis: 
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Get:3 [http://repository.spotify.com](http://repository.spotify.com) stable Release.gpg [490 B]                 
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://repository.spotify.com](http://repository.spotify.com) stable Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                           
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg                 
Ign [http://repository.spotify.com](http://repository.spotify.com) stable Release                               
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free amd64 Packages/DiffIndex     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [106 kB]        
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free i386 Packages/DiffIndex      
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free TranslationIndex             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources/DiffIndex                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494 B] 
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [30.7 kB]   
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,795 B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [401 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages/DiffIndex             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages/DiffIndex              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                     
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free amd64 Packages               
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [4,627 B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [93.5 kB]
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en               
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2,434 B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [427 kB] 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [460 kB]      
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [98.7 kB]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,647 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [8,056 B]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [107 kB] 
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                            
  404  Not Found
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [8,909 B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [789 kB]
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                      
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages  
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en 
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages [13.7 kB]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [241 kB]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [15.3 kB]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [822 kB]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [13.7 kB]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [247 kB]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [15.5 kB]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en     
Fetched 4,029 kB in 10s (395 kB/s)                                             
W: GPG error: [http://repository.spotify.com](http://repository.spotify.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 082CCEDF94558F59
W: Failed to fetch [http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
dennis@dennis1:~$
```

---

### Post by QIII on 2014-06-12
Moved to its own thread from [http://ubuntuforums.org/showthread.php?t=2220956](http://ubuntuforums.org/showthread.php?t=2220956)

Yours is not the same issue as the OP in the other thread.  Please do not hijack the threads of others.

Thanks.

---

### Post by SUPERFITTER on 2014-06-12
OOPS! Sorry!

---

### Post by wildmanne39 on 2014-06-12
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by deadflowr on 2014-06-12
I do not know what's up with the spotify gpg, but it seems cinnamon-stable has been discontinued
More here on that
[http://forums.linuxmint.com/viewtopic.php?f=208&t=169400](http://forums.linuxmint.com/viewtopic.php?f=208&t=169400)

I would open the "update manager", go to "settings", and then in the window that opens, go to "other software" and proceed to uncheck the ppa for cinnamon.

Hope it helps, somewhat.

---

### Post by SUPERFITTER on 2014-06-12
> **deadflowr said:**
> I do not know what's up with the spotify gpg, but it seems cinnamon-stable has been discontinued
More here on that
[http://forums.linuxmint.com/viewtopic.php?f=208&t=169400](http://forums.linuxmint.com/viewtopic.php?f=208&t=169400)

I would open the "update manager", go to "settings", and then in the window that opens, go to "other software" and proceed to uncheck the ppa for cinnamon.

Hope it helps, somewhat.

I unchecked:
W: GPG error: [http://repository.spotify.com](http://repository.spotify.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 082CCEDF94558F59
W: Failed to fetch [http://ppa.launchpad.net/gwendal-leb...source/Sources]("http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/source/Sources")  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/gwendal-leb...amd64/Packages]("http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/binary-amd64/Packages")  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/gwendal-leb...-i386/Packages]("http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/binary-i386/Packages")  404  Not Found

It allowed me to update.  I hope it allows me to update again when new updates appear?

Thank you

---

