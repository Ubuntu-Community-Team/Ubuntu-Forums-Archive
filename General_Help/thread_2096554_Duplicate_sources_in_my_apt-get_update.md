---
title: "Duplicate sources in my apt-get update?"
date: 2012-12-20
forum: General Help
---

### Post by sdowney717 on 2012-12-20
I fixed this once by commenting out some lines in sources  and it has reappeared
This time I fixed by unclicking the CDROM sources!

```
Reading package lists... Done
W: Duplicate sources.list entry cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)/ precise/main i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04.1%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20120823.1)_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)/ precise/restricted i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04.1%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20120823.1)_dists_precise_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
ubun
```


```
ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ InRelease
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ InRelease
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise InRelease
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Release
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Release
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Packages/DiffIndex
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Packages/DiffIndex
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/main/binary-i386/ Translation-en
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) dists/precise/restricted/binary-i386/ Translation-en
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/main TranslationIndex
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/restricted TranslationIndex
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/main Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/main Translation-en
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/restricted Translation-en_US
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1) precise/restricted Translation-en
Ign http://dl.google.com stable InRelease                                      
Ign http://archive.ubuntu.com precise InRelease                                
Ign http://archive.ubuntu.com precise-updates InRelease                        
Hit http://archive.ubuntu.com precise Release.gpg                              
Hit http://dl.google.com stable Release.gpg                                    
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Get:1 http://archive.ubuntu.com precise-updates Release.gpg [198 B]            
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://dl.google.com stable Release                                        
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://archive.ubuntu.com precise Release                                  
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://dl.google.com stable/main amd64 Packages                            
Get:2 http://archive.ubuntu.com precise-updates Release [49.6 kB]              
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release                                   
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://archive.ubuntu.com precise/main amd64 Packages                      
Hit http://archive.ubuntu.com precise/restricted amd64 Packages                
Hit http://archive.ubuntu.com precise/universe amd64 Packages                  
Hit http://archive.ubuntu.com precise/multiverse amd64 Packages                
Hit http://archive.ubuntu.com precise/main i386 Packages                       
Hit http://archive.ubuntu.com precise/restricted i386 Packages                 
Hit http://archive.ubuntu.com precise/universe i386 Packages                   
Hit http://archive.ubuntu.com precise/multiverse i386 Packages                 
Hit http://archive.ubuntu.com precise/main TranslationIndex                    
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex              
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://archive.ubuntu.com precise/restricted TranslationIndex              
Hit http://archive.ubuntu.com precise/universe TranslationIndex                
Get:3 http://archive.ubuntu.com precise-updates/main amd64 Packages [446 kB]   
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:4 http://archive.ubuntu.com precise-updates/restricted amd64 Packages [8,366 B]
Get:5 http://archive.ubuntu.com precise-updates/universe amd64 Packages [163 kB]
Ign http://dl.google.com stable/main Translation-en_US                         
Get:6 http://archive.ubuntu.com precise-updates/multiverse amd64 Packages [8,671 B]
Get:7 http://archive.ubuntu.com precise-updates/main i386 Packages [454 kB]    
Ign http://dl.google.com stable/main Translation-en                            
Ign http://security.ubuntu.com precise-security InRelease                      
Get:8 http://archive.ubuntu.com precise-updates/restricted i386 Packages [8,374 B]
Get:9 http://archive.ubuntu.com precise-updates/universe i386 Packages [165 kB]
Get:10 http://archive.ubuntu.com precise-updates/multiverse i386 Packages [9,675 B]
Hit http://archive.ubuntu.com precise-updates/main TranslationIndex            
Hit http://archive.ubuntu.com precise-updates/multiverse TranslationIndex      
Hit http://archive.ubuntu.com precise-updates/restricted TranslationIndex      
Hit http://archive.ubuntu.com precise-updates/universe TranslationIndex        
Hit http://archive.ubuntu.com precise/main Translation-en                      
Hit http://archive.ubuntu.com precise/multiverse Translation-en                
Hit http://archive.ubuntu.com precise/restricted Translation-en                
Hit http://archive.ubuntu.com precise/universe Translation-en                  
Get:11 http://security.ubuntu.com precise-security Release.gpg [198 B]         
Hit http://archive.ubuntu.com precise-updates/main Translation-en              
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en        
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en        
Hit http://archive.ubuntu.com precise-updates/universe Translation-en          
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Get:12 http://security.ubuntu.com precise-security Release [49.6 kB]
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en 
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en  
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en  
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en  
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en  
Get:13 http://security.ubuntu.com precise-security/main amd64 Packages [214 kB]
Get:14 http://security.ubuntu.com precise-security/restricted amd64 Packages [3,969 B]
Get:15 http://security.ubuntu.com precise-security/universe amd64 Packages [60.1 kB]
Get:16 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,183 B]
Get:17 http://security.ubuntu.com precise-security/main i386 Packages [221 kB] 
Get:18 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:19 http://security.ubuntu.com precise-security/universe i386 Packages [61.1 kB]
Get:20 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,392 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Fetched 1,930 kB in 11s (175 kB/s)                                             
Reading package lists... Done
W: Duplicate sources.list entry cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)/ precise/main i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04.1%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20120823.1)_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)/ precise/restricted i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04.1%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20120823.1)_dists_precise_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
ubuntu@ubuntu:~$ 

```

---

### Post by Pjotr123 on 2012-12-20
That's a dirty sources list.... Yuck. Full of useless PPA's.

I advise to clean it up:
```
sudo apt-get install ppa-purge
```

---

### Post by grahammechanical on 2012-12-20
Do you need to use a Cdrom as a repository (software source)? I don't. I have my Cdrom with Ubuntu 12.10 'Quantal Questzal' also unchecked. I am not having any problems with this. But If I wanted to upgrade to a newer version of Ubuntu from a DVD and not over the Internet then I would have to add the DVD as a software source.

What problems are you having now?

Regards.

P.S. You should be able to use the Remove button to remove one of those duplicate references to the Cdrom.

---

### Post by sdowney717 on 2012-12-20
This is an unusual situation.
I am experimenting with running a LiveUSB on a USB 2.0 hardrive

I am not even sure what all these odd looking ppa are.

---

### Post by sdowney717 on 2012-12-20
snapshot of my other sources

I installed a bunch of gnome themes

---

### Post by wladypauly on 2012-12-20
You could try and comment out or delete one of the two identical lines in /etc/apt/sources.list and then run update again. It happened to me once and I solved it this way.

---

### Post by Pjotr123 on 2012-12-20
> **sdowney717 said:**
> This is an unusual situation.
I am experimenting with running a LiveUSB on a USB 2.0 hardrive


You're not supposed to install updates or any other software, in a Live session. This might be considered as Ubuntu abuse, which is punishable by seven years hard labour in the salt mines of Dzhezkazgan. :p

---

### Post by sdowney717 on 2012-12-20
> **Pjotr123 said:**
> You're not supposed to install updates or any other software, in a Live session. This might be considered as Ubuntu abuse, which is punishable by seven years hard labour in the salt mines of Dzhezkazgan. :p

It all worked very well. I eventually ran out of space.
I was able to install all apps and do updates. I found that the LiveUSB file system is designed to help a flash drive survive, so it slowly uses up all free space. 

I was thinking the convenience of speed running the system for user experience combined with the install ability would make it more realistic experience vs running off a thumb drive which is very slow.

Is there any way you can have an 'install program' which can run off a standard install? Something like an app for the OS. Would be very convenient, do a full install on a portable drive and be able to install onto other systems.

---

### Post by monkeybrain2012 on 2012-12-20
> **sdowney717 said:**
> It all worked very well. I eventually ran out of space.
I was able to install all apps and do updates. I found that the LiveUSB file system is designed to help a flash drive survive, so it slowly uses up all free space. 

I was thinking the convenience of speed running the system for user experience combined with the install ability would make it more realistic experience vs running off a thumb drive which is very slow.

Is there any way you can have an 'install program' which can run off a standard install? Something like an app for the OS. Would be very convenient, do a full install on a portable drive and be able to install onto other systems.

You can do a standard install in a usb flash drive (at least 8 gb if you want to update and install a whole bunch of stuffs so that it works like a real install) But it is kind of slow. So a better way would be to do it on an external hard drive, which gives you the speed and the space and you can also carry it around and boot off different machines.

This is more than detail enough
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

It is about lubuntu (don't know which version) but it is the same with all *buntus and versions with probably some trivial modifications. It is about installing into a flash drive but it is the same for external hard drive.

P.S. live usb with persistence is limited to 4 G (since it uses FAT which supports only up to 4 G) so not surprisingly you run out of space pretty fast.

Another thing, install bleachbit and run  it after installation and update, which will remove a lot of junks like unused language packs which will recover a lot of space.

---

