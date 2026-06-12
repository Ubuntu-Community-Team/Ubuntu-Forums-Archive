---
title: "could someone more knowledgeable take a look at my sources.list plz?"
date: 2013-08-12
forum: General Help
---

### Post by merockstar on 2013-08-12
ok here's my situation.

i got to playing and installed crossover trial, and several alternative desktop environments before deciding that regular old wine, and regular old canonical-backed unity was the way to go for me.

today I got an error saying that my sources.list was jacked up (not all repositories were able to connect).

so I went and unchecked the repositories that said "crossover," or "lxde," then I checked the software manager to see that lxde had indeed been previously uninstalled. then i uninstalled crossover trial through synaptic.

problem seems to be fixed (at least I don't have a triangle with a red question mark in my system tray anymore). but i did notice that a couple of my repositories are still failing.
I also was worried hoping that I didn't inadvertantly remove a critically important repository, so could somebody whose not still learning this stuff take a look at my sources.list, and either reassure me that its fine, or tell me what changes need to be made to bring it back to normalcy?

```

# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)]/ raring main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ raring main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ raring main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ raring universe
deb-src http://us.archive.ubuntu.com/ubuntu/ raring universe
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ raring multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ raring multiverse
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ raring-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu raring-security main restricted
deb-src http://security.ubuntu.com/ubuntu raring-security main restricted
deb http://security.ubuntu.com/ubuntu raring-security universe
deb-src http://security.ubuntu.com/ubuntu raring-security universe
deb http://security.ubuntu.com/ubuntu raring-security multiverse
deb-src http://security.ubuntu.com/ubuntu raring-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu raring partner
# deb-src http://archive.canonical.com/ubuntu raring partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu raring main
deb-src http://extras.ubuntu.com/ubuntu raring main

```

i missed this community. I'm glad to be an ubuntu user again.

---

### Post by bapoumba on 2013-08-12
Looks fine to me. Could you please post the output to** sudo apt-get update** to see which repos give you an error ? Thanks.

---

### Post by ajgreeny on 2013-08-12
Have you added any ppa repos to your sources, which will not show in your sources.list file but as a separate file in the **/etc/apt/sources.list.d** folder.

---

### Post by merockstar on 2013-08-23
bapoumba, i seem to have made the error go away, but am getting alot of Ign now:

```
Hit http://us.archive.ubuntu.com raring Release.gpg
Hit http://repo.steampowered.com precise Release.gpg                                                                                          
Hit http://ppa.launchpad.net raring Release.gpg                                                                                               
Get:1 http://us.archive.ubuntu.com raring-updates Release.gpg [933 B]                                                                  
Hit http://archive.canonical.com raring Release.gpg                                                                                               
Get:2 http://extras.ubuntu.com raring Release.gpg [72 B]                                                         
Hit http://us.archive.ubuntu.com raring-backports Release.gpg                                                                                   
Hit http://repo.steampowered.com precise Release                                                                 
Hit http://us.archive.ubuntu.com raring Release                                                                  
Hit http://security.ubuntu.com raring-security Release.gpg                                                       
Hit http://ppa.launchpad.net raring Release.gpg                                                                                         
Get:3 http://us.archive.ubuntu.com raring-updates Release [40.8 kB]                                                                     
Hit http://archive.canonical.com raring Release                                                                                                   
Hit http://extras.ubuntu.com raring Release                                                                                                       
Hit http://security.ubuntu.com raring-security Release                                                                      
Hit http://ppa.launchpad.net raring Release                                                           
Hit http://us.archive.ubuntu.com raring-backports Release                                    
Hit http://us.archive.ubuntu.com raring/main Sources                                                                                     
Hit http://repo.steampowered.com precise/steam Sources                                                                                   
Hit http://us.archive.ubuntu.com raring/restricted Sources                                                                                                             
Hit http://ppa.launchpad.net raring Release                                                                                                                            
Hit http://us.archive.ubuntu.com raring/universe Sources                                                                                                               
Hit http://archive.canonical.com raring/partner amd64 Packages                                                                                                         
Hit http://extras.ubuntu.com raring/main Sources                                                                                                                       
Hit http://security.ubuntu.com raring-security/main Sources                                                                                                            
Hit http://us.archive.ubuntu.com raring/multiverse Sources                                                                                                     
Hit http://us.archive.ubuntu.com raring/main amd64 Packages                                                                                                    
Hit http://ppa.launchpad.net raring/main amd64 Packages                                                                                 
Hit http://repo.steampowered.com precise/steam amd64 Packages                                                                           
Hit http://archive.canonical.com raring/partner i386 Packages                                                                                                          
Hit http://us.archive.ubuntu.com raring/restricted amd64 Packages                                                                                                      
Hit http://extras.ubuntu.com raring/main amd64 Packages                                                                                            
Hit http://security.ubuntu.com raring-security/restricted Sources                                                                                                      
Hit http://us.archive.ubuntu.com raring/universe amd64 Packages                                                                                                        
Hit http://us.archive.ubuntu.com raring/multiverse amd64 Packages                                                                                                      
Hit http://ppa.launchpad.net raring/main i386 Packages                                                                                                                 
Hit http://extras.ubuntu.com raring/main i386 Packages                                                                                  
Hit http://security.ubuntu.com raring-security/universe Sources                                                   
Hit http://us.archive.ubuntu.com raring/main i386 Packages                                                        
Hit http://us.archive.ubuntu.com raring/restricted i386 Packages                                                                        
Hit http://repo.steampowered.com precise/steam i386 Packages                                                                            
Hit http://security.ubuntu.com raring-security/multiverse Sources                                                 
Hit http://us.archive.ubuntu.com raring/universe i386 Packages                                                                                                         
Hit http://security.ubuntu.com raring-security/main amd64 Packages                                                                                                     
Hit http://us.archive.ubuntu.com raring/multiverse i386 Packages                                                                        
Hit http://us.archive.ubuntu.com raring/main Translation-en                                                                             
Hit http://security.ubuntu.com raring-security/restricted amd64 Packages                                                                
Hit http://ppa.launchpad.net raring/main amd64 Packages                                                           
Hit http://us.archive.ubuntu.com raring/multiverse Translation-en                                                 
Hit https://private-ppa.launchpad.net raring Release.gpg                                                          
Hit http://security.ubuntu.com raring-security/universe amd64 Packages                                                                  
Hit http://ppa.launchpad.net raring/main i386 Packages                                                                                  
Hit http://us.archive.ubuntu.com raring/restricted Translation-en                           
Hit http://security.ubuntu.com raring-security/multiverse amd64 Packages                                          
Hit http://us.archive.ubuntu.com raring/universe Translation-en                                                   
Hit https://private-ppa.launchpad.net raring Release                                                              
Get:4 http://us.archive.ubuntu.com raring-updates/main Sources [62.0 kB]                                                                                       
Hit http://security.ubuntu.com raring-security/main i386 Packages                                                                                                  
Hit http://security.ubuntu.com raring-security/restricted i386 Packages                                                                          
Get:5 http://us.archive.ubuntu.com raring-updates/restricted Sources [14 B]                                                                                   
Get:6 http://us.archive.ubuntu.com raring-updates/universe Sources [70.9 kB]                                                                                  
Hit https://private-ppa.launchpad.net raring/main amd64 Packages                                                           
Hit http://security.ubuntu.com raring-security/universe i386 Packages                                                      
Ign http://archive.canonical.com raring/partner Translation-en_US                                                                       
Get:7 http://us.archive.ubuntu.com raring-updates/multiverse Sources [2,264 B]                                                          
Hit http://security.ubuntu.com raring-security/multiverse i386 Packages                                                                                       
Get:8 http://us.archive.ubuntu.com raring-updates/main amd64 Packages [158 kB]                                                          
Hit https://private-ppa.launchpad.net raring/main i386 Packages                                                                             
Ign http://extras.ubuntu.com raring/main Translation-en_US                                                                                       
Ign http://archive.canonical.com raring/partner Translation-en                                                                                   
Ign http://extras.ubuntu.com raring/main Translation-en                                                                    
Hit http://security.ubuntu.com raring-security/main Translation-en                           
Get:9 http://us.archive.ubuntu.com raring-updates/restricted amd64 Packages [14 B]           
Get:10 http://us.archive.ubuntu.com raring-updates/universe amd64 Packages [137 kB]                                   
Get:11 http://us.archive.ubuntu.com raring-updates/multiverse amd64 Packages [3,702 B]                              
Hit http://security.ubuntu.com raring-security/multiverse Translation-en                      
Get:12 http://us.archive.ubuntu.com raring-updates/main i386 Packages [157 kB]
Ign http://repo.steampowered.com precise/steam Translation-en_US                                     
Get:13 http://us.archive.ubuntu.com raring-updates/restricted i386 Packages [14 B]                                  
Ign http://repo.steampowered.com precise/steam Translation-en                                                           
Hit http://security.ubuntu.com raring-security/restricted Translation-en                      
Get:14 http://us.archive.ubuntu.com raring-updates/universe i386 Packages [138 kB]            
Get:15 http://us.archive.ubuntu.com raring-updates/multiverse i386 Packages [3,871 B]
Hit http://security.ubuntu.com raring-security/universe Translation-en                                     
Hit http://us.archive.ubuntu.com raring-updates/main Translation-en   
Hit http://us.archive.ubuntu.com raring-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com raring-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com raring-updates/universe Translation-en
Hit http://us.archive.ubuntu.com raring-backports/main Sources        
Hit http://us.archive.ubuntu.com raring-backports/restricted Sources  
Hit http://us.archive.ubuntu.com raring-backports/universe Sources    
Hit http://us.archive.ubuntu.com raring-backports/multiverse Sources  
Ign http://ppa.launchpad.net raring/main Translation-en_US
Hit http://us.archive.ubuntu.com raring-backports/main amd64 Packages
Ign http://ppa.launchpad.net raring/main Translation-en
Hit http://us.archive.ubuntu.com raring-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com raring-backports/universe amd64 Packages
Ign http://ppa.launchpad.net raring/main Translation-en_US            
Hit http://us.archive.ubuntu.com raring-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com raring-backports/main i386 Packages  
Hit http://us.archive.ubuntu.com raring-backports/restricted i386 Packages
Ign http://ppa.launchpad.net raring/main Translation-en               
Hit http://us.archive.ubuntu.com raring-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com raring-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com raring-backports/main Translation-en
Hit http://us.archive.ubuntu.com raring-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com raring-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com raring-backports/universe Translation-en
Ign http://security.ubuntu.com raring-security/main Translation-en_US
Ign http://security.ubuntu.com raring-security/multiverse Translation-en_US
Ign http://security.ubuntu.com raring-security/restricted Translation-en_US
Ign http://security.ubuntu.com raring-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com raring/main Translation-en_US
Ign http://us.archive.ubuntu.com raring/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com raring/restricted Translation-en_US
Ign http://us.archive.ubuntu.com raring/universe Translation-en_US                                                                                                     
Ign http://us.archive.ubuntu.com raring-updates/main Translation-en_US                                                                                                 
Ign http://us.archive.ubuntu.com raring-updates/multiverse Translation-en_US                                                                                           
Ign http://us.archive.ubuntu.com raring-updates/restricted Translation-en_US                                                                                           
Ign http://us.archive.ubuntu.com raring-updates/universe Translation-en_US                                                                                             
Ign http://us.archive.ubuntu.com raring-backports/main Translation-en_US                                                                                               
Ign http://us.archive.ubuntu.com raring-backports/multiverse Translation-en_US                                                                                         
Ign http://us.archive.ubuntu.com raring-backports/restricted Translation-en_US                                                                                         
Ign http://us.archive.ubuntu.com raring-backports/universe Translation-en_US                                                                                           
Ign https://private-ppa.launchpad.net raring/main Translation-en_US                                                                                                    
Ign https://private-ppa.launchpad.net raring/main Translation-en    
```


ajgreeny:

```
bitcoin-bitcoin-raring.list	  private-ppa.launchpad.net_commercial-ppa-uploaders_crossover-trial_ubuntu.list
bitcoin-bitcoin-raring.list.save  private-ppa.launchpad.net_commercial-ppa-uploaders_crossover-trial_ubuntu.list.save
linrunner-tlp-raring.list	  private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list
linrunner-tlp-raring.list.save	  private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.save
lxde-ppa-raring.list		  steam.list
lxde-ppa-raring.list.save	  steam.list.save

```

are those files save to remove if i no longer use the program? (i dont use lxde or crossover anymore, and cant remember what linrunner is)

sorry for the delayed response. thanks for your help guys!

---

