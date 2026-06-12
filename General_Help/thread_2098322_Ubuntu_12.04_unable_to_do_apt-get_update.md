---
title: "Ubuntu 12.04 unable to do apt-get update"
date: 2012-12-26
forum: General Help
---

### Post by quailstorm on 2012-12-26
Hello guys!

Firstly, I'm Hungarian, as you'll se in screenshots, and I've got an issue related to apt system in ubuntu. If I press check for updates in Update manager, it gets stuck at 100%, but if I press cancel, I'm able to install a bunch of updates.
Also if I do apt-get update in x-terminal, it gets stuck at 99%, after downloading package informations.
Maybe it would like to say "waiting for headlines", but the kernel messages are also Hungarian...

[IMG]http://img189.imageshack.us/img189/8292/updatefail.png[/IMG]

I've tried to change servers... Also this issue is 11 days old as you can see.

Terminal message:

```
quail@STORMINTER-8:~$ sudo apt-get update
[sudo] password for quail: 
Mell&#337;z http://dl.google.com stable InRelease
Mell&#337;z http://extras.ubuntu.com precise InRelease                              
Mell&#337;z http://archive.canonical.com precise InRelease                          
Mell&#337;z http://ppa.launchpad.net precise InRelease                              
Mell&#337;z http://ppa.launchpad.net precise InRelease                              
Mell&#337;z http://ppa.launchpad.net precise InRelease                              
Találat http://dl.google.com stable Release.gpg                                
Mell&#337;z http://archive.ubuntu.com precise InRelease                             
Mell&#337;z http://archive.ubuntu.com precise-updates InRelease                     
Mell&#337;z http://archive.ubuntu.com precise-backports InRelease                   
Mell&#337;z http://archive.ubuntu.com precise-security InRelease                    
Mell&#337;z http://archive.ubuntu.com precise-proposed InRelease                    
Mell&#337;z http://deb.opera.com stable InRelease                                   
Mell&#337;z http://deb.opera.com stable InRelease                                   
Találat http://extras.ubuntu.com precise Release.gpg                           
Találat http://archive.canonical.com precise Release.gpg                       
Találat http://ppa.launchpad.net precise Release.gpg                           
Találat http://dl.google.com stable Release                                    
Találat http://archive.ubuntu.com precise Release.gpg                          
Találat http://extras.ubuntu.com precise Release                               
Találat http://archive.canonical.com precise Release                           
Találat http://ppa.launchpad.net precise Release.gpg                           
Találat http://deb.opera.com stable Release.gpg                                
Találat http://archive.ubuntu.com precise-updates Release.gpg                  
Találat http://archive.ubuntu.com precise-backports Release.gpg                
Találat http://archive.ubuntu.com precise-security Release.gpg                 
Találat http://dl.google.com stable/main amd64 Packages                        
Találat http://extras.ubuntu.com precise/main Sources                          
Találat http://ppa.launchpad.net precise Release.gpg                           
Találat http://archive.canonical.com precise/partner Sources                   
Találat http://deb.opera.com stable Release.gpg                                
Találat http://archive.ubuntu.com precise-proposed Release.gpg                 
Találat http://dl.google.com stable/main i386 Packages                         
Találat http://extras.ubuntu.com precise/main amd64 Packages                   
Mell&#337;z http://dl.google.com stable/main TranslationIndex                       
Találat http://extras.ubuntu.com precise/main i386 Packages                    
Mell&#337;z http://extras.ubuntu.com precise/main TranslationIndex                  
Találat http://ppa.launchpad.net precise Release                               
Találat http://archive.canonical.com precise/partner amd64 Packages            
Találat http://archive.canonical.com precise/partner i386 Packages             
Mell&#337;z http://archive.canonical.com precise/partner TranslationIndex           
Találat http://archive.ubuntu.com precise Release                              
Találat http://archive.ubuntu.com precise-updates Release                      
Találat http://archive.ubuntu.com precise-backports Release                    
Találat http://deb.opera.com stable Release                                    
Találat http://ppa.launchpad.net precise Release                               
Találat http://archive.ubuntu.com precise-security Release                     
Találat http://ppa.launchpad.net precise Release                               
Találat http://deb.opera.com stable Release                                    
Találat http://archive.ubuntu.com precise-proposed Release                     
Találat http://archive.ubuntu.com precise/main Sources                         
Találat http://archive.ubuntu.com precise/restricted Sources                   
Találat http://archive.ubuntu.com precise/multiverse Sources                   
Találat http://archive.ubuntu.com precise/universe Sources                     
Találat http://archive.ubuntu.com precise/main amd64 Packages                  
Találat http://ppa.launchpad.net precise/main Sources                          
Találat http://ppa.launchpad.net precise/main amd64 Packages                   
Találat http://ppa.launchpad.net precise/main i386 Packages                    
Mell&#337;z http://ppa.launchpad.net precise/main TranslationIndex                  
Találat http://archive.ubuntu.com precise/restricted amd64 Packages            
Találat http://archive.ubuntu.com precise/universe amd64 Packages              
Találat http://archive.ubuntu.com precise/multiverse amd64 Packages            
Találat http://archive.ubuntu.com precise/main i386 Packages                   
Találat http://deb.opera.com stable/non-free amd64 Packages                    
Találat http://deb.opera.com stable/non-free i386 Packages                     
Mell&#337;z http://deb.opera.com stable/non-free TranslationIndex                   
Találat http://archive.ubuntu.com precise/restricted i386 Packages             
Találat http://archive.ubuntu.com precise/universe i386 Packages               
Találat http://archive.ubuntu.com precise/multiverse i386 Packages             
Találat http://archive.ubuntu.com precise/main TranslationIndex                
Találat http://archive.ubuntu.com precise/multiverse TranslationIndex          
Találat http://ppa.launchpad.net precise/main Sources                          
Találat http://ppa.launchpad.net precise/main amd64 Packages                   
Találat http://ppa.launchpad.net precise/main i386 Packages                    
Mell&#337;z http://ppa.launchpad.net precise/main TranslationIndex                  
Találat http://archive.ubuntu.com precise/restricted TranslationIndex          
Találat http://deb.opera.com stable/non-free amd64 Packages                    
Találat http://deb.opera.com stable/non-free i386 Packages                     
Mell&#337;z http://deb.opera.com stable/non-free TranslationIndex                   
Találat http://archive.ubuntu.com precise/universe TranslationIndex            
Találat http://archive.ubuntu.com precise-updates/restricted Sources           
Találat http://archive.ubuntu.com precise-updates/main Sources                 
Találat http://archive.ubuntu.com precise-updates/multiverse Sources           
Találat http://archive.ubuntu.com precise-updates/universe Sources             
Találat http://ppa.launchpad.net precise/main Sources                          
Találat http://ppa.launchpad.net precise/main amd64 Packages                   
Találat http://ppa.launchpad.net precise/main i386 Packages                    
Mell&#337;z http://ppa.launchpad.net precise/main TranslationIndex                  
Találat http://archive.ubuntu.com precise-updates/main amd64 Packages          
Találat http://archive.ubuntu.com precise-updates/restricted amd64 Packages    
Találat http://archive.ubuntu.com precise-updates/universe amd64 Packages      
Találat http://archive.ubuntu.com precise-updates/multiverse amd64 Packages    
Találat http://archive.ubuntu.com precise-updates/main i386 Packages           
Találat http://archive.ubuntu.com precise-updates/restricted i386 Packages     
Találat http://archive.ubuntu.com precise-updates/universe i386 Packages       
Találat http://archive.ubuntu.com precise-updates/multiverse i386 Packages     
Találat http://archive.ubuntu.com precise-updates/main TranslationIndex        
Találat http://archive.ubuntu.com precise-updates/multiverse TranslationIndex  
Találat http://archive.ubuntu.com precise-updates/restricted TranslationIndex  
Találat http://archive.ubuntu.com precise-updates/universe TranslationIndex    
Találat http://archive.ubuntu.com precise-backports/main Sources               
Találat http://archive.ubuntu.com precise-backports/restricted Sources         
Találat http://archive.ubuntu.com precise-backports/universe Sources           
Találat http://archive.ubuntu.com precise-backports/multiverse Sources         
Találat http://archive.ubuntu.com precise-backports/main amd64 Packages        
Találat http://archive.ubuntu.com precise-backports/restricted amd64 Packages  
Találat http://archive.ubuntu.com precise-backports/universe amd64 Packages    
Találat http://archive.ubuntu.com precise-backports/multiverse amd64 Packages  
Találat http://archive.ubuntu.com precise-backports/main i386 Packages         
Találat http://archive.ubuntu.com precise-backports/restricted i386 Packages   
Találat http://archive.ubuntu.com precise-backports/universe i386 Packages     
Találat http://archive.ubuntu.com precise-backports/multiverse i386 Packages   
Találat http://archive.ubuntu.com precise-backports/main TranslationIndex      
Találat http://archive.ubuntu.com precise-backports/multiverse TranslationIndex
Találat http://archive.ubuntu.com precise-backports/restricted TranslationIndex
Találat http://archive.ubuntu.com precise-backports/universe TranslationIndex  
Találat http://archive.ubuntu.com precise-security/restricted Sources          
Találat http://archive.ubuntu.com precise-security/main Sources                
Találat http://archive.ubuntu.com precise-security/multiverse Sources          
Találat http://archive.ubuntu.com precise-security/universe Sources            
Találat http://archive.ubuntu.com precise-security/main amd64 Packages         
Találat http://archive.ubuntu.com precise-security/restricted amd64 Packages   
Találat http://archive.ubuntu.com precise-security/universe amd64 Packages     
Találat http://archive.ubuntu.com precise-security/multiverse amd64 Packages   
Találat http://archive.ubuntu.com precise-security/main i386 Packages          
Találat http://archive.ubuntu.com precise-security/restricted i386 Packages    
Találat http://archive.ubuntu.com precise-security/universe i386 Packages      
Találat http://archive.ubuntu.com precise-security/multiverse i386 Packages    
Találat http://archive.ubuntu.com precise-security/main TranslationIndex       
Találat http://archive.ubuntu.com precise-security/multiverse TranslationIndex 
Találat http://archive.ubuntu.com precise-security/restricted TranslationIndex 
Találat http://archive.ubuntu.com precise-security/universe TranslationIndex   
Találat http://archive.ubuntu.com precise-proposed/restricted Sources          
Találat http://archive.ubuntu.com precise-proposed/main Sources                
Találat http://archive.ubuntu.com precise-proposed/multiverse Sources          
Találat http://archive.ubuntu.com precise-proposed/universe Sources            
Találat http://archive.ubuntu.com precise-proposed/restricted amd64 Packages   
Találat http://archive.ubuntu.com precise-proposed/main amd64 Packages         
Találat http://archive.ubuntu.com precise-proposed/multiverse amd64 Packages   
Találat http://archive.ubuntu.com precise-proposed/universe amd64 Packages     
Mell&#337;z http://extras.ubuntu.com precise/main Translation-hu_HU                 
Találat http://archive.ubuntu.com precise-proposed/restricted i386 Packages    
Találat http://archive.ubuntu.com precise-proposed/main i386 Packages          
Találat http://archive.ubuntu.com precise-proposed/multiverse i386 Packages    
Mell&#337;z http://archive.canonical.com precise/partner Translation-hu_HU          
Találat http://archive.ubuntu.com precise-proposed/universe i386 Packages      
Találat http://archive.ubuntu.com precise-proposed/main TranslationIndex       
Találat http://archive.ubuntu.com precise-proposed/multiverse TranslationIndex 
Találat http://archive.ubuntu.com precise-proposed/restricted TranslationIndex 
Találat http://archive.ubuntu.com precise-proposed/universe TranslationIndex   
Mell&#337;z http://extras.ubuntu.com precise/main Translation-hu                    
Találat http://archive.ubuntu.com precise/main Translation-hu                  
Találat http://archive.ubuntu.com precise/main Translation-en                  
Mell&#337;z http://archive.canonical.com precise/partner Translation-hu             
Találat http://archive.ubuntu.com precise/multiverse Translation-hu            
Találat http://archive.ubuntu.com precise/multiverse Translation-en            
Találat http://archive.ubuntu.com precise/restricted Translation-hu            
Találat http://archive.ubuntu.com precise/restricted Translation-en            
Mell&#337;z http://extras.ubuntu.com precise/main Translation-en                    
Mell&#337;z http://archive.canonical.com precise/partner Translation-en             
Mell&#337;z http://deb.opera.com stable/non-free Translation-hu_HU                  
Mell&#337;z http://deb.opera.com stable/non-free Translation-hu                     
Mell&#337;z http://ppa.launchpad.net precise/main Translation-hu_HU                 
Mell&#337;z http://ppa.launchpad.net precise/main Translation-hu                    
Mell&#337;z http://deb.opera.com stable/non-free Translation-en                     
Mell&#337;z http://deb.opera.com stable/non-free Translation-hu_HU                  
Találat http://archive.ubuntu.com precise/universe Translation-hu              
Találat http://archive.ubuntu.com precise/universe Translation-en              
Találat http://archive.ubuntu.com precise-updates/main Translation-hu          
Találat http://archive.ubuntu.com precise-updates/main Translation-en          
Találat http://archive.ubuntu.com precise-updates/multiverse Translation-hu    
Találat http://archive.ubuntu.com precise-updates/multiverse Translation-en    
Találat http://archive.ubuntu.com precise-updates/restricted Translation-hu    
Találat http://archive.ubuntu.com precise-updates/restricted Translation-en    
Találat http://archive.ubuntu.com precise-updates/universe Translation-hu      
Mell&#337;z http://ppa.launchpad.net precise/main Translation-en                    
Mell&#337;z http://ppa.launchpad.net precise/main Translation-hu_HU                 
Mell&#337;z http://ppa.launchpad.net precise/main Translation-hu                    
Mell&#337;z http://ppa.launchpad.net precise/main Translation-en                    
Mell&#337;z http://ppa.launchpad.net precise/main Translation-hu_HU                 
Mell&#337;z http://deb.opera.com stable/non-free Translation-hu                     
Mell&#337;z http://deb.opera.com stable/non-free Translation-en                     
Találat http://archive.ubuntu.com precise-updates/universe Translation-en      
Találat http://archive.ubuntu.com precise-backports/main Translation-en        
Találat http://archive.ubuntu.com precise-backports/multiverse Translation-en  
Találat http://archive.ubuntu.com precise-backports/restricted Translation-en  
Találat http://archive.ubuntu.com precise-backports/universe Translation-en    
Találat http://archive.ubuntu.com precise-security/main Translation-en         
Mell&#337;z http://ppa.launchpad.net precise/main Translation-hu                    
Mell&#337;z http://ppa.launchpad.net precise/main Translation-en                    
Mell&#337;z http://dl.google.com stable/main Translation-hu_HU                      
Mell&#337;z http://dl.google.com stable/main Translation-hu                         
Találat http://archive.ubuntu.com precise-security/multiverse Translation-en   
Találat http://archive.ubuntu.com precise-security/restricted Translation-en
Találat http://archive.ubuntu.com precise-security/universe Translation-en
Találat http://archive.ubuntu.com precise-proposed/main Translation-hu
Találat http://archive.ubuntu.com precise-proposed/main Translation-en
Találat http://archive.ubuntu.com precise-proposed/multiverse Translation-hu   
Mell&#337;z http://dl.google.com stable/main Translation-en                         
Találat http://archive.ubuntu.com precise-proposed/multiverse Translation-en   
Találat http://archive.ubuntu.com precise-proposed/restricted Translation-hu
Találat http://archive.ubuntu.com precise-proposed/restricted Translation-en
Találat http://archive.ubuntu.com precise-proposed/universe Translation-hu
Találat http://archive.ubuntu.com precise-proposed/universe Translation-en
99% [Várakozás a fejlécekre]
```

---

### Post by Frogs Hair on 2012-12-26
Proposed updates are for testing and have been known to cause problems with the package system though I have had none in five releases. This Looks like be the problem, but with the package list reaching 99% the offending source or package isn't displayed. Try the following and maybe the problem will be identified. ```
sudo apt-get update && sudo apt-get upgrade 
```
I would say disable proposed updates, but that will affect further updates to software installed via proposed updates.

---

### Post by quailstorm on 2012-12-26
Proposed updates has no effect. I've tried it...
Now I'll reboot and try what you've mentioned. But I don't think it will say more.
EDIT: no further data from terminal. Same as above.

---

### Post by quailstorm on 2013-02-05
If anyone is curious, I did an apt-get dist-upgrade, and currently I use a working Ubuntu 12.10 without any loss of data.

---

