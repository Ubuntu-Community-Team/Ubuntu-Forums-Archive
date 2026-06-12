---
title: "unable to get updates for 12.04"
date: 2013-12-22
forum: General Help
---

### Post by deaton25 on 2013-12-22
i can't get all my updates for ubuntu 12.04
i get 404's for four of them 
failed to download files or could not fetch from canonical archives
something about network connection problems maybe?....or repository problems?
but my wi-fi network connection seems fine....
but now i'm getting the little red triangle with the exclamation mark in the middle

can you help? i don' t know anything about computers

thanks

---

### Post by sammiev on 2013-12-22
run the code in terminal and post the results here so we can read the errors. Use the code tags (#) please.

```
sudo apt-get update
```

---

### Post by deaton25 on 2013-12-22
```
alan@alan-Latitude-D530:~$ sudo apt-get update
[sudo] password for alan: 
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg                              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise Release.gpg                           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates Release.gpg                   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports Release.gpg                 
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release                                  
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Ign [http://archive.canonical.com](http://archive.canonical.com) ubuntu Release.gpg                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources                       
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) ubuntu Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed Release.gpg                  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise Release                               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates Release                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports Release                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main Sources                          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe Sources                      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe TranslationIndex             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/restricted Sources            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main Sources                  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/multiverse Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Ign [http://archive.canonical.com](http://archive.canonical.com) ubuntu/partner TranslationIndex               
Ign [http://archive.canonical.com](http://archive.canonical.com) ubuntu/precise TranslationIndex               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe Sources              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main i386 Packages            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/restricted i386 Packages      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe i386 Packages        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/multiverse i386 Packages      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/main Sources                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/restricted Sources          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/universe Sources            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/multiverse Sources          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/main i386 Packages          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/restricted i386 Packages    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/universe i386 Packages      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/multiverse i386 Packages    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/main TranslationIndex       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/multiverse TranslationIndex 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/restricted Sources           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/main Sources                 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/multiverse Sources           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/universe Sources             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/restricted i386 Packages     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/main i386 Packages           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/multiverse i386 Packages     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/universe i386 Packages       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/main TranslationIndex        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/multiverse TranslationIndex  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/restricted TranslationIndex  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/universe TranslationIndex    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main Translation-en_CA                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe Translation-en_CA            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe Translation-en               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_CA                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main Translation-en_CA        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main Translation-en           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/restricted Translation-en     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe Translation-en_CA    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe Translation-en       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/restricted Translation-en   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/universe Translation-en     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/main Translation-en_CA       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/main Translation-en          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/multiverse Translation-en    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/restricted Translation-en    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/universe Translation-en_CA   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-proposed/universe Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_CA          
Err [http://archive.canonical.com](http://archive.canonical.com) ubuntu/precise Sources              
  404  Not Found [IP: 91.189.92.191 80]
Err [http://archive.canonical.com](http://archive.canonical.com) ubuntu/partner Sources
  404  Not Found [IP: 91.189.92.191 80]
Err [http://archive.canonical.com](http://archive.canonical.com) ubuntu/precise i386 Packages
  404  Not Found [IP: 91.189.92.191 80]
Err [http://archive.canonical.com](http://archive.canonical.com) ubuntu/partner i386 Packages
  404  Not Found [IP: 91.189.92.191 80]
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_CA   
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en             
Ign [http://archive.canonical.com](http://archive.canonical.com) ubuntu/partner Translation-en_CA
Ign [http://archive.canonical.com](http://archive.canonical.com) ubuntu/partner Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) ubuntu/precise Translation-en_CA
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_CA
Ign [http://archive.canonical.com](http://archive.canonical.com) ubuntu/precise Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_CA
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_CA
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_CA
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_CA
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_CA
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
W: Failed to fetch [http://archive.canonical.com/dists/ubuntu/precise/source/Sources](http://archive.canonical.com/dists/ubuntu/precise/source/Sources)  404  Not Found [IP: 91.189.92.191 80]


W: Failed to fetch [http://archive.canonical.com/dists/ubuntu/partner/source/Sources](http://archive.canonical.com/dists/ubuntu/partner/source/Sources)  404  Not Found [IP: 91.189.92.191 80]


W: Failed to fetch [http://archive.canonical.com/dists/ubuntu/precise/binary-i386/Packages](http://archive.canonical.com/dists/ubuntu/precise/binary-i386/Packages)  404  Not Found [IP: 91.189.92.191 80]


W: Failed to fetch [http://archive.canonical.com/dists/ubuntu/partner/binary-i386/Packages](http://archive.canonical.com/dists/ubuntu/partner/binary-i386/Packages)  404  Not Found [IP: 91.189.92.191 80]


E: Some index files failed to download. They have been ignored, or old ones used instead.
alan@alan-Latitude-D530:~$
```

---

### Post by Bashing-om on 2013-12-22
deaton25; Hi !

Looks like you have bad formats in some of the index lines in that control file.

If you need advise on what/where to edit that file(s), post back to us the output of terminal commands:
```

cat -n /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list

```

[INDENT][INDENT]so a tale is told
[/INDENT][/INDENT]

---

### Post by deaton25 on 2013-12-22
```
alan@alan-Latitude-D530:~$ cat -n /etc/apt/sources.list
     1	# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820.1)]/ precise main restricted
     2	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted #Added by software-properties
     3	
     4	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     5	# newer versions of the distribution.
     6	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise main restricted
     7	deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise restricted main multiverse universe #Added by software-properties
     8	
     9	## Major bug fix updates produced after the final release of the
    10	## distribution.
    11	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates main restricted
    12	deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates restricted main multiverse universe #Added by software-properties
    13	
    14	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    15	## team. Also, please note that software in universe WILL NOT receive any
    16	## review or updates from the Ubuntu security team.
    17	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise universe
    18	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates universe
    19	
    20	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    21	## team, and may not be under a free licence. Please satisfy yourself as to 
    22	## your rights to use the software. Also, please note that software in 
    23	## multiverse WILL NOT receive any review or updates from the Ubuntu
    24	## security team.
    25	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise multiverse
    26	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates multiverse
    27	
    28	## N.B. software from this repository may not have been tested as
    29	## extensively as that contained in the main release, although it includes
    30	## newer versions of some applications which may provide useful features.
    31	## Also, please note that software in backports WILL NOT receive any review
    32	## or updates from the Ubuntu security team.
    33	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
    34	deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse #Added by software-properties
    35	
    36	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
    37	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security restricted main multiverse universe #Added by software-properties
    38	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
    39	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
    40	
    41	## Uncomment the following two lines to add software from Canonical's
    42	## 'partner' repository.
    43	## This software is not part of Ubuntu, but is offered by Canonical and the
    44	## respective vendors as a service to Ubuntu users.
    45	deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    46	deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    47	
    48	## This software is not part of Ubuntu, but is offered by third-party
    49	## developers who want to ship their latest software.
    50	deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
    51	deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
    52	deb [http://archive.canonical.com/](http://archive.canonical.com/) ubuntu precise partner
    53	deb-src [http://archive.canonical.com/](http://archive.canonical.com/) ubuntu precise partner
    54	deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-proposed restricted main multiverse universe
    55	deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-proposed restricted main multiverse universe #Added by software-properties
```
```
alan@alan-Latitude-D530:~$ cat /etc/apt/sources.list.d/*.list
deb [http://ppa.launchpad.net/atareao/atareao/ubuntu](http://ppa.launchpad.net/atareao/atareao/ubuntu) precise main
deb-src [http://ppa.launchpad.net/atareao/atareao/ubuntu](http://ppa.launchpad.net/atareao/atareao/ubuntu) precise main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
deb [http://ppa.launchpad.net/hydr0g3n/qbittorrent-stable/ubuntu](http://ppa.launchpad.net/hydr0g3n/qbittorrent-stable/ubuntu) precise main
deb-src [http://ppa.launchpad.net/hydr0g3n/qbittorrent-stable/ubuntu](http://ppa.launchpad.net/hydr0g3n/qbittorrent-stable/ubuntu) precise main
deb [http://ppa.launchpad.net/pywapi-devel/ppa/ubuntu](http://ppa.launchpad.net/pywapi-devel/ppa/ubuntu) precise main
deb-src [http://ppa.launchpad.net/pywapi-devel/ppa/ubuntu](http://ppa.launchpad.net/pywapi-devel/ppa/ubuntu) precise main
deb [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) precise main
deb-src [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) precise main
deb [http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu](http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu) precise main
deb-src [http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu](http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu) precise main
deb [http://ppa.launchpad.net/zedtux/naturalscrolling/ubuntu](http://ppa.launchpad.net/zedtux/naturalscrolling/ubuntu) precise main
deb-src [http://ppa.launchpad.net/zedtux/naturalscrolling/ubuntu](http://ppa.launchpad.net/zedtux/naturalscrolling/ubuntu) precise main
alan@alan-Latitude-D530:~$
```

---

### Post by Bashing-om on 2013-12-22
deaton25; Well,

All looks to be in order, I see no fault:
So:
> 
We all know what http code 404 means: File does not exist in the place you are looking for it.
That's not an Ubuntu failure. You likely just caught the repository during an update.
Try it again.
(ian-weisser)


Is the thing to do.
```

sudo apt-get update
sudo apt-get upgrade

```

[INDENT][INDENT]good tidings
[/INDENT][/INDENT]

---

### Post by deaton25 on 2013-12-22
thank you!

---

### Post by Bashing-om on 2013-12-22
deaton25; Welcome;

If you are presently updated and all is good,
Please mark this thread as solved - 1st post -> thread tools - aids others seeking a solution and helps keep the forum tidy.

ubuntu
[INDENT][INDENT]all for one and 1 for all[/INDENT][/INDENT]

---

### Post by sammiev on 2013-12-22
It seems your error is from this line.

```
deb http://dl.google.com/linux/chrome/deb/ stable main
```

I get a 404 error from that line.

I see your getting good help. :)

---

### Post by deaton25 on 2013-12-25
Actually, the problem was not solved until i did this
[http://askubuntu.com/questions/65911/how-can-i-fix-a-404-error-when-updating-packages](http://askubuntu.com/questions/65911/how-can-i-fix-a-404-error-when-updating-packages)
this did the trick at last!

---

