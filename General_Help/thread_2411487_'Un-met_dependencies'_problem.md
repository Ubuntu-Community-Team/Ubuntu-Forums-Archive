---
title: "'Un-met dependencies' problem"
date: 2019-01-30
forum: General Help
---

### Post by grey1beard on 2019-01-30
I'm running 14.04, and today noticed the 'no entry' icon on the task bar.
I opened a terminal and ran apt-get upgrade, and got the following

```
john@john-RM:~$ sudo apt-get upgrade
[sudo] password for john: 
Reading package lists... Error!
E: Unable to parse package file /var/lib/apt/lists/la-mirrors.evowise.com_ubuntu_dists_trusty_Release (1)
E: Problem opening /var/lib/apt/lists/la-mirrors.evowise.com_ubuntu_dists_trusty_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
```

I then tried running apt-get update, -
```
john@john-RM:~$ sudo apt-get update
Ign http://dl.google.com stable InRelease                                      
Get:1 http://dl.google.com stable Release.gpg [819 B]                          
Hit http://dl.google.com stable Release                                        
Hit http://ppa.launchpad.net trusty InRelease                                  
Ign http://dl.google.com stable Release                                        
Ign http://download.ebz.epson.net lsb3.2 InRelease                             
Ign http://dl.google.com stable/main i386 Packages/DiffIndex                   
Hit http://download.ebz.epson.net lsb3.2 Release.gpg                           
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://download.ebz.epson.net lsb3.2 Release                               
Ign http://dl.google.com stable/main Translation-en_GB                         
Ign http://dl.google.com stable/main Translation-en                            
Hit http://download.ebz.epson.net lsb3.2/main i386 Packages                    
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://download.ebz.epson.net lsb3.2/main Translation-en_GB                
Hit http://ppa.launchpad.net trusty/main Sources                               
Hit http://download.ebz.epson.net lsb3.2/main Translation-en                   
Ign http://la-mirrors.evowise.com trusty InRelease                             
Hit http://la-mirrors.evowise.com trusty-updates InRelease                     
Hit http://la-mirrors.evowise.com trusty-security InRelease                    
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:2 http://la-mirrors.evowise.com trusty Release.gpg [933 B]                 
Hit http://la-mirrors.evowise.com trusty-updates/main Sources                  
Hit http://la-mirrors.evowise.com trusty-updates/restricted Sources            
Hit http://la-mirrors.evowise.com trusty-updates/universe Sources              
Hit http://la-mirrors.evowise.com trusty-updates/multiverse Sources            
Get:3 http://la-mirrors.evowise.com trusty-updates/main i386 Packages [1,065 kB]
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://la-mirrors.evowise.com trusty-updates/multiverse i386 Packages      
Hit http://la-mirrors.evowise.com trusty-updates/main Translation-en           
Hit http://la-mirrors.evowise.com trusty-updates/multiverse Translation-en     
Hit http://la-mirrors.evowise.com trusty-updates/restricted Translation-en     
Hit http://la-mirrors.evowise.com trusty-updates/universe Translation-en       
Hit http://la-mirrors.evowise.com trusty Release                               
Ign http://la-mirrors.evowise.com trusty Release                               
Hit http://la-mirrors.evowise.com trusty-security/main Sources                 
Hit http://la-mirrors.evowise.com trusty-security/restricted Sources           
Hit http://la-mirrors.evowise.com trusty-security/universe Sources             
Hit http://la-mirrors.evowise.com trusty-security/multiverse Sources           
Hit http://la-mirrors.evowise.com trusty-security/main i386 Packages           
Hit http://la-mirrors.evowise.com trusty-security/restricted i386 Packages     
Hit http://la-mirrors.evowise.com trusty-security/universe i386 Packages       
Hit http://la-mirrors.evowise.com trusty-security/multiverse i386 Packages     
Hit http://la-mirrors.evowise.com trusty-security/main Translation-en          
Hit http://la-mirrors.evowise.com trusty-security/multiverse Translation-en    
Hit http://la-mirrors.evowise.com trusty-security/restricted Translation-en    
Hit http://ppa.launchpad.net trusty/main Sources                               
Hit http://la-mirrors.evowise.com trusty-security/universe Translation-en      
Hit http://la-mirrors.evowise.com trusty-updates/restricted i386 Packages      
Hit http://la-mirrors.evowise.com trusty-updates/universe i386 Packages        
Hit http://la-mirrors.evowise.com trusty/main Sources/DiffIndex                
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1397BC53640DB551
W: GPG error: http://la-mirrors.evowise.com trusty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
E: Unable to parse package file /var/lib/apt/lists/la-mirrors.evowise.com_ubuntu_dists_trusty_main_source_Sources.IndexDiff (1)
```

I'd be very grateful for any help in what my next step(s) should be.
John

---

### Post by Claus7 on 2019-01-31
Hello,

why don't you try to change the server where the updates are downloaded from? Checking from here:
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

sooner or later 14.04 will reach end of life though. 

Synaptic Package Manager -> Settings -> Repositories -> Downloaded from...

Regards!

---

### Post by grey1beard on 2019-03-17
> **Claus7 said:**
> Hello,

why don't you try to change the server where the updates are downloaded from? Checking from here:
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

sooner or later 14.04 will reach end of life though. 

Synaptic Package Manager -> Settings -> Repositories -> Downloaded from...

Regards!

Sorry for the delay in my replying to your post.
I've tried your suggestion, but immediately ran into a brick wall !
(See attached)
John

---

### Post by again? on 2019-03-17
Open software properties from terminal and choose the main server or "other" and select another local mirror.
```
software-properties-gtk
```

---

### Post by grey1beard on 2019-03-17
Many thanks. Now making progress, and I'll post a heads up when I get to the finishing line !
Regards,
John

---

