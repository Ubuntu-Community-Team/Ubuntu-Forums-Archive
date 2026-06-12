---
title: "&quot;W:Failed to fetch&quot; &quot;404  Not Found&quot; &quot;&quot;"
date: 2014-05-16
forum: General Help
---

### Post by xp15 on 2014-05-16
I cant Update, I tried many thing, I think my /etc/apt/sources.list file is not correct (Got the idea from here: [http://askubuntu.com/questions/439264/unable-to-get-updated-package-information-apt-get-update-xubuntu-12-04](http://askubuntu.com/questions/439264/unable-to-get-updated-package-information-apt-get-update-xubuntu-12-04) , and: there: [http://ubuntuforums.org/showthread.php?t=2046145](http://ubuntuforums.org/showthread.php?t=2046145))

Here is my file content:
```
# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://releases.ubuntu.spd.co.il/ precise main restricted
deb-src http://releases.ubuntu.spd.co.il/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://releases.ubuntu.spd.co.il/ precise-updates main restricted
deb-src http://releases.ubuntu.spd.co.il/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://releases.ubuntu.spd.co.il/ precise universe
deb-src http://releases.ubuntu.spd.co.il/ precise universe
deb http://releases.ubuntu.spd.co.il/ precise-updates universe
deb-src http://releases.ubuntu.spd.co.il/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://releases.ubuntu.spd.co.il/ precise multiverse
deb-src http://releases.ubuntu.spd.co.il/ precise multiverse
deb http://releases.ubuntu.spd.co.il/ precise-updates multiverse
deb-src http://releases.ubuntu.spd.co.il/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://releases.ubuntu.spd.co.il/ precise-backports main restricted universe multiverse
deb-src http://releases.ubuntu.spd.co.il/ precise-backports main restricted universe multiverse

deb http://releases.ubuntu.spd.co.il/ precise-security main restricted
deb-src http://releases.ubuntu.spd.co.il/ precise-security main restricted
deb http://releases.ubuntu.spd.co.il/ precise-security universe
deb-src http://releases.ubuntu.spd.co.il/ precise-security universe
deb http://releases.ubuntu.spd.co.il/ precise-security multiverse
deb-src http://releases.ubuntu.spd.co.il/ precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
```

What Should I do? More solutions? I can give back output.
Please tell me what's the problem and how to fix it, so ext time I will be able to solve it.

Thanks guys, Love you, Oh hey girl, Love you too... What are you doing tonight? Oh hahahahaha you funny. Well I'll be busy fixing my meighbors ubunutu-pc.

---

### Post by plucky on 2014-05-16
Is this actually **[SOLVED]**?

If Not, run ```
sudo apt-get update
``` and post the output.

Good Luck

---

### Post by xp15 on 2014-05-16
oh no, sorry! mistake! it's not solved. Ill fix it! EDIT: I can't ): All I can is marking this thread as Solved... The irony... (Please someome change it to Ubuntu [12.04 LTS])
Here is the output of "sudo apt-get update":
```
hila@Hila:~$ sudo apt-get update
[sudo] password for hila: 
Sorry, try again.
[sudo] password for hila: 
Sorry, try again.
[sudo] password for hila: 
Hit http://releases.ubuntu.spd.co.il precise Release.gpg
Hit http://releases.ubuntu.spd.co.il precise-updates Release.gpg               
Hit http://dl.google.com stable Release.gpg                                    
Hit http://releases.ubuntu.spd.co.il precise-backports Release.gpg             
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://releases.ubuntu.spd.co.il precise-security Release.gpg              
Hit http://dl.google.com stable Release                                        
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://releases.ubuntu.spd.co.il precise Release                           
Hit http://ppa.launchpad.net precise Release                                   
Hit http://extras.ubuntu.com precise Release                                   
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://releases.ubuntu.spd.co.il precise-updates Release                   
Ign http://dl.google.com stable/main Translation-he_IL                         
Ign http://dl.google.com stable/main Translation-he                            
Ign http://dl.google.com stable/main Translation-en                            
Hit http://releases.ubuntu.spd.co.il precise-backports Release                 
Hit http://releases.ubuntu.spd.co.il precise-security Release                  
Hit http://releases.ubuntu.spd.co.il precise/main Sources                      
Hit http://releases.ubuntu.spd.co.il precise/restricted Sources                
Hit http://releases.ubuntu.spd.co.il precise/universe Sources                  
Hit http://releases.ubuntu.spd.co.il precise/multiverse Sources                
Hit http://releases.ubuntu.spd.co.il precise/main i386 Packages                
Hit http://releases.ubuntu.spd.co.il precise/restricted i386 Packages      
Hit http://releases.ubuntu.spd.co.il precise/universe i386 Packages            
Ign http://extras.ubuntu.com precise/main Translation-he_IL                    
Ign http://extras.ubuntu.com precise/main Translation-he                       
Ign http://ppa.launchpad.net precise/main Translation-he_IL                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-he                       
Hit http://releases.ubuntu.spd.co.il precise/multiverse i386 Packages          
Hit http://releases.ubuntu.spd.co.il precise/main TranslationIndex             
Hit http://releases.ubuntu.spd.co.il precise/multiverse TranslationIndex
Hit http://releases.ubuntu.spd.co.il precise/restricted TranslationIndex
Hit http://releases.ubuntu.spd.co.il precise/universe TranslationIndex
Hit http://releases.ubuntu.spd.co.il precise-updates/main Sources
Get:1 http://releases.ubuntu.spd.co.il precise-updates/restricted Sources [8,028 B]
Get:2 http://releases.ubuntu.spd.co.il precise-updates/restricted Sources [8,028 B]
Get:3 http://releases.ubuntu.spd.co.il precise-updates/restricted Sources [8,028 B]
Get:4 http://releases.ubuntu.spd.co.il precise-updates/restricted Sources [8,028 B]
Hit http://releases.ubuntu.spd.co.il precise-updates/universe Sources         
Hit http://releases.ubuntu.spd.co.il precise-updates/multiverse Sources
Ign http://ppa.launchpad.net precise/main Translation-en
Hit http://releases.ubuntu.spd.co.il precise-updates/main i386 Packages
Hit http://releases.ubuntu.spd.co.il precise-updates/restricted i386 Packages
Hit http://releases.ubuntu.spd.co.il precise-updates/universe i386 Packages
Hit http://releases.ubuntu.spd.co.il precise-updates/multiverse i386 Packages
Hit http://releases.ubuntu.spd.co.il precise-updates/main TranslationIndex
Hit http://releases.ubuntu.spd.co.il precise-updates/multiverse TranslationIndex
Hit http://releases.ubuntu.spd.co.il precise-updates/restricted TranslationIndex
Hit http://releases.ubuntu.spd.co.il precise-updates/universe TranslationIndex
Hit http://releases.ubuntu.spd.co.il precise-backports/main Sources
Hit http://releases.ubuntu.spd.co.il precise-backports/restricted Sources
Hit http://releases.ubuntu.spd.co.il precise-backports/universe Sources
Hit http://releases.ubuntu.spd.co.il precise-backports/multiverse Sources
Hit http://releases.ubuntu.spd.co.il precise-backports/main i386 Packages
Hit http://releases.ubuntu.spd.co.il precise-backports/restricted i386 Packages
Hit http://releases.ubuntu.spd.co.il precise-backports/universe i386 Packages
Hit http://releases.ubuntu.spd.co.il precise-backports/multiverse i386 Packages
Hit http://releases.ubuntu.spd.co.il precise-backports/main TranslationIndex
Hit http://releases.ubuntu.spd.co.il precise-backports/multiverse TranslationIndex
Hit http://releases.ubuntu.spd.co.il precise-backports/restricted TranslationIndex
Hit http://releases.ubuntu.spd.co.il precise-backports/universe TranslationIndex
Hit http://releases.ubuntu.spd.co.il precise-security/main Sources
Hit http://releases.ubuntu.spd.co.il precise-security/restricted Sources
Hit http://releases.ubuntu.spd.co.il precise-security/universe Sources
Hit http://releases.ubuntu.spd.co.il precise-security/multiverse Sources
Hit http://releases.ubuntu.spd.co.il precise-security/main i386 Packages
Hit http://releases.ubuntu.spd.co.il precise-security/restricted i386 Packages
Hit http://releases.ubuntu.spd.co.il precise-security/universe i386 Packages
Hit http://releases.ubuntu.spd.co.il precise-security/multiverse i386 Packages
Hit http://releases.ubuntu.spd.co.il precise-security/main TranslationIndex
Hit http://releases.ubuntu.spd.co.il precise-security/multiverse TranslationIndex
Hit http://releases.ubuntu.spd.co.il precise-security/restricted TranslationIndex
Hit http://releases.ubuntu.spd.co.il precise-security/universe TranslationIndex
Hit http://releases.ubuntu.spd.co.il precise/main Translation-en
Hit http://releases.ubuntu.spd.co.il precise/multiverse Translation-he         
Hit http://releases.ubuntu.spd.co.il precise/multiverse Translation-en         
Hit http://releases.ubuntu.spd.co.il precise/restricted Translation-he         
Hit http://releases.ubuntu.spd.co.il precise/restricted Translation-en         
Hit http://releases.ubuntu.spd.co.il precise/universe Translation-he           
Hit http://releases.ubuntu.spd.co.il precise/universe Translation-en           
Hit http://releases.ubuntu.spd.co.il precise-updates/main Translation-en       
Hit http://releases.ubuntu.spd.co.il precise-updates/multiverse Translation-he 
Hit http://releases.ubuntu.spd.co.il precise-updates/multiverse Translation-en 
Hit http://releases.ubuntu.spd.co.il precise-updates/restricted Translation-he 
Hit http://releases.ubuntu.spd.co.il precise-updates/restricted Translation-en 
Hit http://releases.ubuntu.spd.co.il precise-updates/universe Translation-he
Hit http://releases.ubuntu.spd.co.il precise-updates/universe Translation-en
Hit http://releases.ubuntu.spd.co.il precise-backports/main Translation-en
Hit http://releases.ubuntu.spd.co.il precise-backports/multiverse Translation-en
Hit http://releases.ubuntu.spd.co.il precise-backports/restricted Translation-en
Hit http://releases.ubuntu.spd.co.il precise-backports/universe Translation-en
Hit http://releases.ubuntu.spd.co.il precise-security/main Translation-en
Hit http://releases.ubuntu.spd.co.il precise-security/multiverse Translation-en
Hit http://releases.ubuntu.spd.co.il precise-security/restricted Translation-en
Hit http://releases.ubuntu.spd.co.il precise-security/universe Translation-en
Err http://releases.ubuntu.spd.co.il precise-updates/restricted Sources
  404  Not Found
Fetched 8,028 B in 20s (388 B/s)                                
W: &#1499;&#1513;&#1500;&#1493;&#1503; &#1489;&#1492;&#1489;&#1488;&#1514; http://releases.ubuntu.spd.co.il/dists/precise-updates/restricted/source/Sources  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
hila@Hila:~$ 

hila@Hila:~$ sudo apt-get update
[sudo] password for hila: 
Sorry, try again.
[sudo] password for hila: 
Sorry, try again.
[sudo] password for hila: 
Hit http://releases.ubuntu.spd.co.il precise Release.gpg
Hit http://releases.ubuntu.spd.co.il precise-updates Release.gpg               
Hit http://dl.google.com stable Release.gpg                                    
Hit http://releases.ubuntu.spd.co.il precise-backports Release.gpg             
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://releases.ubuntu.spd.co.il precise-security Release.gpg              
Hit http://dl.google.com stable Release                                        
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://releases.ubuntu.spd.co.il precise Release                           
Hit http://ppa.launchpad.net precise Release                                   
Hit http://extras.ubuntu.com precise Release                                   
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://releases.ubuntu.spd.co.il precise-updates Release                   
Ign http://dl.google.com stable/main Translation-he_IL                         
Ign http://dl.google.com stable/main Translation-he                            
Ign http://dl.google.com stable/main Translation-en                            
Hit http://releases.ubuntu.spd.co.il precise-backports Release                 
Hit http://releases.ubuntu.spd.co.il precise-security Release                  
Hit http://releases.ubuntu.spd.co.il precise/main Sources                      
Hit http://releases.ubuntu.spd.co.il precise/restricted Sources                
Hit http://releases.ubuntu.spd.co.il precise/universe Sources                  
Hit http://releases.ubuntu.spd.co.il precise/multiverse Sources                
Hit http://releases.ubuntu.spd.co.il precise/main i386 Packages                
Hit http://releases.ubuntu.spd.co.il precise/restricted i386 Packages      
Hit http://releases.ubuntu.spd.co.il precise/universe i386 Packages            
Ign http://extras.ubuntu.com precise/main Translation-he_IL                    
Ign http://extras.ubuntu.com precise/main Translation-he                       
Ign http://ppa.launchpad.net precise/main Translation-he_IL                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-he                       
Hit http://releases.ubuntu.spd.co.il precise/multiverse i386 Packages          
Hit http://releases.ubuntu.spd.co.il precise/main TranslationIndex             
Hit http://releases.ubuntu.spd.co.il precise/multiverse TranslationIndex
Hit http://releases.ubuntu.spd.co.il precise/restricted TranslationIndex
Hit http://releases.ubuntu.spd.co.il precise/universe TranslationIndex
Hit http://releases.ubuntu.spd.co.il precise-updates/main Sources
Get:1 http://releases.ubuntu.spd.co.il precise-updates/restricted Sources [8,028 B]
Get:2 http://releases.ubuntu.spd.co.il precise-updates/restricted Sources [8,028 B]
Get:3 http://releases.ubuntu.spd.co.il precise-updates/restricted Sources [8,028 B]
Get:4 http://releases.ubuntu.spd.co.il precise-updates/restricted Sources [8,028 B]
Hit http://releases.ubuntu.spd.co.il precise-updates/universe Sources         
Hit http://releases.ubuntu.spd.co.il precise-updates/multiverse Sources
Ign http://ppa.launchpad.net precise/main Translation-en
Hit http://releases.ubuntu.spd.co.il precise-updates/main i386 Packages
Hit http://releases.ubuntu.spd.co.il precise-updates/restricted i386 Packages
Hit http://releases.ubuntu.spd.co.il precise-updates/universe i386 Packages
Hit http://releases.ubuntu.spd.co.il precise-updates/multiverse i386 Packages
Hit http://releases.ubuntu.spd.co.il precise-updates/main TranslationIndex
Hit http://releases.ubuntu.spd.co.il precise-updates/multiverse TranslationIndex
Hit http://releases.ubuntu.spd.co.il precise-updates/restricted TranslationIndex
Hit http://releases.ubuntu.spd.co.il precise-updates/universe TranslationIndex
Hit http://releases.ubuntu.spd.co.il precise-backports/main Sources
Hit http://releases.ubuntu.spd.co.il precise-backports/restricted Sources
Hit http://releases.ubuntu.spd.co.il precise-backports/universe Sources
Hit http://releases.ubuntu.spd.co.il precise-backports/multiverse Sources
Hit http://releases.ubuntu.spd.co.il precise-backports/main i386 Packages
Hit http://releases.ubuntu.spd.co.il precise-backports/restricted i386 Packages
Hit http://releases.ubuntu.spd.co.il precise-backports/universe i386 Packages
Hit http://releases.ubuntu.spd.co.il precise-backports/multiverse i386 Packages
Hit http://releases.ubuntu.spd.co.il precise-backports/main TranslationIndex
Hit http://releases.ubuntu.spd.co.il precise-backports/multiverse TranslationIndex
Hit http://releases.ubuntu.spd.co.il precise-backports/restricted TranslationIndex
Hit http://releases.ubuntu.spd.co.il precise-backports/universe TranslationIndex
Hit http://releases.ubuntu.spd.co.il precise-security/main Sources
Hit http://releases.ubuntu.spd.co.il precise-security/restricted Sources
Hit http://releases.ubuntu.spd.co.il precise-security/universe Sources
Hit http://releases.ubuntu.spd.co.il precise-security/multiverse Sources
Hit http://releases.ubuntu.spd.co.il precise-security/main i386 Packages
Hit http://releases.ubuntu.spd.co.il precise-security/restricted i386 Packages
Hit http://releases.ubuntu.spd.co.il precise-security/universe i386 Packages
Hit http://releases.ubuntu.spd.co.il precise-security/multiverse i386 Packages
Hit http://releases.ubuntu.spd.co.il precise-security/main TranslationIndex
Hit http://releases.ubuntu.spd.co.il precise-security/multiverse TranslationIndex
Hit http://releases.ubuntu.spd.co.il precise-security/restricted TranslationIndex
Hit http://releases.ubuntu.spd.co.il precise-security/universe TranslationIndex
Hit http://releases.ubuntu.spd.co.il precise/main Translation-en
Hit http://releases.ubuntu.spd.co.il precise/multiverse Translation-he         
Hit http://releases.ubuntu.spd.co.il precise/multiverse Translation-en         
Hit http://releases.ubuntu.spd.co.il precise/restricted Translation-he         
Hit http://releases.ubuntu.spd.co.il precise/restricted Translation-en         
Hit http://releases.ubuntu.spd.co.il precise/universe Translation-he           
Hit http://releases.ubuntu.spd.co.il precise/universe Translation-en           
Hit http://releases.ubuntu.spd.co.il precise-updates/main Translation-en       
Hit http://releases.ubuntu.spd.co.il precise-updates/multiverse Translation-he 
Hit http://releases.ubuntu.spd.co.il precise-updates/multiverse Translation-en 
Hit http://releases.ubuntu.spd.co.il precise-updates/restricted Translation-he 
Hit http://releases.ubuntu.spd.co.il precise-updates/restricted Translation-en 
Hit http://releases.ubuntu.spd.co.il precise-updates/universe Translation-he
Hit http://releases.ubuntu.spd.co.il precise-updates/universe Translation-en
Hit http://releases.ubuntu.spd.co.il precise-backports/main Translation-en
Hit http://releases.ubuntu.spd.co.il precise-backports/multiverse Translation-en
Hit http://releases.ubuntu.spd.co.il precise-backports/restricted Translation-en
Hit http://releases.ubuntu.spd.co.il precise-backports/universe Translation-en
Hit http://releases.ubuntu.spd.co.il precise-security/main Translation-en
Hit http://releases.ubuntu.spd.co.il precise-security/multiverse Translation-en
Hit http://releases.ubuntu.spd.co.il precise-security/restricted Translation-en
Hit http://releases.ubuntu.spd.co.il precise-security/universe Translation-en
Err http://releases.ubuntu.spd.co.il precise-updates/restricted Sources
  404  Not Found
Fetched 8,028 B in 20s (388 B/s)                                
W: &#1499;&#1513;&#1500;&#1493;&#1503; &#1489;&#1492;&#1489;&#1488;&#1514; http://releases.ubuntu.spd.co.il/dists/precise-updates/restricted/source/Sources  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
hila@Hila:~$ 


```

---

### Post by plucky on 2014-05-16
> W: &#1499;&#1513;&#1500;&#1493;&#1503; &#1489;&#1492;&#1489;&#1488;&#1514; [http://releases.ubuntu.spd.co.il/dists/precise-updates/restricted/source/Sources](http://releases.ubuntu.spd.co.il/dists/precise-updates/restricted/source/Sources)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

There is a problem with that repository on your local server.

You could try changing (temporarily) to the "Main Server" ( or a different local server) in Software Sources and see if you get the same problem.

There is a possibility that the server is out of sync with the main server,which will probably correct itself if you wait a day or so.


Good Luck

---

### Post by xp15 on 2014-05-16
Give you the output?

---

### Post by xp15 on 2014-05-17
Didn't help (Told you I already tried the easy solutions):
```
hila@Hilasudo apt-get update
[sudo] password for hila: 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release.gpg                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release.gpg                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release                                  
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release                          
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release                        
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Sources                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-he_IL          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Sources                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-he_IL                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-he                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-he                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-he_IL                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex                 
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-he
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-he
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-he
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-he
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-he
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-he
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-he
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe i386 Packages [48.0 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Translation-en          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Translation-en
Fetched 1 B in 15s (0 B/s)
W: &#1499;&#1513;&#1500;&#1493;&#1503; &#1489;&#1492;&#1489;&#1488;&#1514; gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-backports_universe_binary-i386_Packages  Hash Sum mismatch **(Hebrew part means "FAILED IN GETTING [...]")**

E: Some index files failed to download. They have been ignored, or old ones used instead.
hila@Hila:~$
```

---

### Post by ibjsb4 on 2014-05-17
Got the answer in the that next to last line.

This should work for you.

[http://ubuntuforums.org/showthread.php?t=2224326&p=13026211#post13026211](http://ubuntuforums.org/showthread.php?t=2224326&p=13026211#post13026211)

Why is this thread marked solved?

---

### Post by deadflowr on 2014-05-17
I removed the solved tag.
Please mark it again as solved when it is actually solved, please.

---

### Post by ibjsb4 on 2014-05-17
In case your wondering ..

[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

---

### Post by xp15 on 2014-05-17
What do you mean by "Got the answer in the that next to last line." ? You mean that by my output you think this will solve it?
Didnt help. I've run the commands, here output after running them (you can see them done):

```
hila@Hila:~$ sudo apt-get clean
[sudo] password for hila: 
hila@Hila:~$ sudo mv /var/lib/apt/lists /var/lib/apt/lists.broke
hila@Hila:~$ sudo mkdir -p /var/lib/apt/lists/partial
hila@Hila:~$ sudo apt-get update
Get:1 http://archive.ubuntu.com precise Release.gpg [198 B]                    
Get:2 http://dl.google.com stable Release.gpg [198 B]                          
Get:3 http://ppa.launchpad.net precise Release.gpg [316 B]                     
Get:4 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Get:5 http://archive.ubuntu.com precise-updates Release.gpg [198 B]            
Get:6 http://dl.google.com stable Release [1,351 B]                            
Get:7 http://archive.ubuntu.com precise-backports Release.gpg [198 B]          
Get:8 http://extras.ubuntu.com precise Release [11.9 kB]                       
Get:9 http://ppa.launchpad.net precise Release [11.9 kB]                       
Get:10 http://dl.google.com stable/main i386 Packages [1,245 B]                
Get:11 http://archive.ubuntu.com precise-security Release.gpg [198 B]          
Get:12 http://extras.ubuntu.com precise/main Sources [8,130 B]                 
Get:13 http://ppa.launchpad.net precise/main Sources [6,637 B]                 
Ign http://dl.google.com stable/main TranslationIndex                          
Get:14 http://ppa.launchpad.net precise/main i386 Packages [7,518 B]           
Get:15 http://extras.ubuntu.com precise/main i386 Packages [10.8 kB]           
Get:16 http://archive.ubuntu.com precise Release [49.6 kB]                     
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Get:17 http://archive.ubuntu.com precise Release [49.6 kB]                     
Get:18 http://archive.ubuntu.com precise-updates Release [49.6 kB]             
Get:19 http://archive.ubuntu.com precise-updates Release [49.6 kB]             
Get:20 http://archive.ubuntu.com precise-backports Release [49.6 kB]           
Get:21 http://archive.ubuntu.com precise-security Release [49.6 kB]            
Ign http://dl.google.com stable/main Translation-he_IL                         
Get:22 http://archive.ubuntu.com precise/main Sources [934 kB]                 
Ign http://dl.google.com stable/main Translation-he                            
Ign http://dl.google.com stable/main Translation-en                            
Ign http://extras.ubuntu.com precise/main Translation-he_IL                    
Ign http://ppa.launchpad.net precise/main Translation-he_IL                    
Get:23 http://archive.ubuntu.com precise/main Sources [934 kB]                 
Ign http://extras.ubuntu.com precise/main Translation-he                       
Ign http://ppa.launchpad.net precise/main Translation-he                       
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en                       
Get:24 http://archive.ubuntu.com precise/restricted Sources [5,470 B]          
Get:25 http://archive.ubuntu.com precise/universe Sources [5,019 kB]           
Get:26 http://archive.ubuntu.com precise/universe Sources [5,019 kB]           
Get:27 http://archive.ubuntu.com precise/universe Sources [5,019 kB]           
Get:28 http://archive.ubuntu.com precise/universe Sources [5,019 kB]           
Get:29 http://archive.ubuntu.com precise/multiverse Sources [155 kB]           
Get:30 http://archive.ubuntu.com precise/multiverse Sources [155 kB]           
Get:31 http://archive.ubuntu.com precise/multiverse Sources [155 kB]           
Get:32 http://archive.ubuntu.com precise/multiverse Sources [155 kB]           
Get:33 http://archive.ubuntu.com precise/main i386 Packages [1,274 kB]         
Get:34 http://archive.ubuntu.com precise/main i386 Packages [1,274 kB]         
Get:35 http://archive.ubuntu.com precise/main i386 Packages [1,274 kB]         
Get:36 http://archive.ubuntu.com precise/main i386 Packages [1,274 kB]         
Get:37 http://archive.ubuntu.com precise/main i386 Packages [1,274 kB]         
Get:38 http://archive.ubuntu.com precise/restricted i386 Packages [8,431 B]    
Get:39 http://archive.ubuntu.com precise/restricted i386 Packages [8,431 B]    
Get:40 http://archive.ubuntu.com precise/restricted i386 Packages [8,431 B]    
Get:41 http://archive.ubuntu.com precise/restricted i386 Packages [8,431 B]    
Get:42 http://archive.ubuntu.com precise/universe i386 Packages [4,796 kB]     
Get:43 http://archive.ubuntu.com precise/universe i386 Packages [4,796 kB]     
Get:44 http://archive.ubuntu.com precise/universe i386 Packages [4,796 kB]     
Get:45 http://archive.ubuntu.com precise/universe i386 Packages [4,796 kB]     
Get:46 http://archive.ubuntu.com precise/multiverse i386 Packages [121 kB]     
Get:47 http://archive.ubuntu.com precise/multiverse i386 Packages [121 kB]     
Get:48 http://archive.ubuntu.com precise/main TranslationIndex [3,706 B]       
Get:49 http://archive.ubuntu.com precise/multiverse TranslationIndex [2,676 B] 
Get:50 http://archive.ubuntu.com precise/restricted TranslationIndex [2,596 B] 
Get:51 http://archive.ubuntu.com precise/universe TranslationIndex [2,922 B]   
Get:52 http://archive.ubuntu.com precise-updates/main Sources [458 kB]         
Get:53 http://archive.ubuntu.com precise-updates/main Sources [458 kB]         
Get:54 http://archive.ubuntu.com precise-updates/restricted Sources [8,028 B]  
Get:55 http://archive.ubuntu.com precise-updates/restricted Sources [8,028 B]  
Get:56 http://archive.ubuntu.com precise-updates/restricted Sources [8,028 B]  
Get:57 http://archive.ubuntu.com precise-updates/restricted Sources [8,028 B]  
Get:58 http://archive.ubuntu.com precise-updates/restricted Sources [8,028 B]  
Get:59 http://archive.ubuntu.com precise-updates/restricted Sources [8,028 B]  
Get:60 http://archive.ubuntu.com precise-updates/restricted Sources [8,028 B]  
Get:61 http://archive.ubuntu.com precise-updates/restricted Sources [8,028 B]  
Get:62 http://archive.ubuntu.com precise-updates/restricted Sources [8,028 B]  
Get:63 http://archive.ubuntu.com precise-updates/universe Sources [107 kB]     
Get:64 http://archive.ubuntu.com precise-updates/universe Sources [107 kB]     
Get:65 http://archive.ubuntu.com precise-updates/multiverse Sources [8,902 B]  
Get:66 http://archive.ubuntu.com precise-updates/multiverse Sources [8,902 B]  
Get:67 http://archive.ubuntu.com precise-updates/multiverse Sources [8,902 B]  
Get:68 http://archive.ubuntu.com precise-updates/multiverse Sources [8,902 B]  
Get:69 http://archive.ubuntu.com precise-updates/main i386 Packages [806 kB]   
Get:70 http://archive.ubuntu.com precise-updates/main i386 Packages [806 kB]   
Get:71 http://archive.ubuntu.com precise-updates/main i386 Packages [806 kB]   
Get:72 http://archive.ubuntu.com precise-updates/main i386 Packages [806 kB]   
Get:73 http://archive.ubuntu.com precise-updates/main i386 Packages [806 kB]   
Get:74 http://archive.ubuntu.com precise-updates/main i386 Packages [806 kB]   
Get:75 http://archive.ubuntu.com precise-updates/restricted i386 Packages [12.2 kB]
Get:76 http://archive.ubuntu.com precise-updates/universe i386 Packages [246 kB]
Get:77 http://archive.ubuntu.com precise-updates/universe i386 Packages [246 kB]
Get:78 http://archive.ubuntu.com precise-updates/universe i386 Packages [246 kB]
Get:79 http://archive.ubuntu.com precise-updates/multiverse i386 Packages [15.5 kB]
Get:80 http://archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:81 http://archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:82 http://archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:83 http://archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Get:84 http://archive.ubuntu.com precise-backports/main Sources [5,145 B]      
Get:85 http://archive.ubuntu.com precise-backports/restricted Sources [14 B]   
Get:86 http://archive.ubuntu.com precise-backports/universe Sources [37.8 kB]  
Get:87 http://archive.ubuntu.com precise-backports/universe Sources [37.8 kB]  
Get:88 http://archive.ubuntu.com precise-backports/multiverse Sources [5,311 B]
Get:89 http://archive.ubuntu.com precise-backports/main i386 Packages [6,420 B]
Get:90 http://archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:91 http://archive.ubuntu.com precise-backports/universe i386 Packages [39.0 kB]
Get:92 http://archive.ubuntu.com precise-backports/universe i386 Packages [39.0 kB]
Get:93 http://archive.ubuntu.com precise-backports/multiverse i386 Packages [5,178 B]
Get:94 http://archive.ubuntu.com precise-backports/main TranslationIndex [72 B]
Get:95 http://archive.ubuntu.com precise-backports/multiverse TranslationIndex [72 B]
Get:96 http://archive.ubuntu.com precise-backports/restricted TranslationIndex [70 B]
Get:97 http://archive.ubuntu.com precise-backports/universe TranslationIndex [73 B]
Get:98 http://archive.ubuntu.com precise-security/main Sources [104 kB]        
Get:99 http://archive.ubuntu.com precise-security/main Sources [104 kB]        
Get:100 http://archive.ubuntu.com precise-security/main Sources [104 kB]       
Get:101 http://archive.ubuntu.com precise-security/restricted Sources [2,494 B]
Get:102 http://archive.ubuntu.com precise-security/universe Sources [30.9 kB]  
Get:103 http://archive.ubuntu.com precise-security/universe Sources [30.9 kB]  
Get:104 http://archive.ubuntu.com precise-security/multiverse Sources [1,794 B]
Get:105 http://archive.ubuntu.com precise-security/main i386 Packages [414 kB] 
Get:106 http://archive.ubuntu.com precise-security/main i386 Packages [414 kB] 
Get:107 http://archive.ubuntu.com precise-security/main i386 Packages [414 kB] 
Get:108 http://archive.ubuntu.com precise-security/main i386 Packages [414 kB] 
Get:109 http://archive.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:110 http://archive.ubuntu.com precise-security/universe i386 Packages [97.6 kB]
Get:111 http://archive.ubuntu.com precise-security/universe i386 Packages [97.6 kB]
Get:112 http://archive.ubuntu.com precise-security/universe i386 Packages [97.6 kB]
Get:113 http://archive.ubuntu.com precise-security/multiverse i386 Packages [2,636 B]
Get:114 http://archive.ubuntu.com precise-security/main TranslationIndex [74 B]
Get:115 http://archive.ubuntu.com precise-security/multiverse TranslationIndex [72 B]
Get:116 http://archive.ubuntu.com precise-security/restricted TranslationIndex [72 B]
Get:117 http://archive.ubuntu.com precise-security/universe TranslationIndex [73 B]
Get:118 http://archive.ubuntu.com precise/main Translation-en [726 kB]         
Get:119 http://archive.ubuntu.com precise/multiverse Translation-he [723 B]    
Get:120 http://archive.ubuntu.com precise/multiverse Translation-en [93.4 kB]  
Get:121 http://archive.ubuntu.com precise/multiverse Translation-en [93.4 kB]  
Get:122 http://archive.ubuntu.com precise/restricted Translation-he [798 B]    
Get:123 http://archive.ubuntu.com precise/restricted Translation-en [2,395 B]  
Get:124 http://archive.ubuntu.com precise/universe Translation-he [381 B]      
Get:125 http://archive.ubuntu.com precise/universe Translation-en [3,341 kB]   
Get:126 http://archive.ubuntu.com precise/universe Translation-en [3,341 kB]   
Get:127 http://archive.ubuntu.com precise/universe Translation-en [3,341 kB]   
Get:128 http://archive.ubuntu.com precise/universe Translation-en [3,341 kB]   
Get:129 http://archive.ubuntu.com precise-updates/main Translation-en [347 kB] 
Get:130 http://archive.ubuntu.com precise-updates/multiverse Translation-he [723 B]
Get:131 http://archive.ubuntu.com precise-updates/multiverse Translation-en [9,010 B]
Get:132 http://archive.ubuntu.com precise-updates/restricted Translation-he [798 B]
Get:133 http://archive.ubuntu.com precise-updates/restricted Translation-en [2,988 B]
Get:134 http://archive.ubuntu.com precise-updates/universe Translation-he [381 B]
Get:135 http://archive.ubuntu.com precise-updates/universe Translation-en [140 kB]
Get:136 http://archive.ubuntu.com precise-backports/main Translation-en [5,882 B]
Get:137 http://archive.ubuntu.com precise-backports/multiverse Translation-en [4,610 B]
Get:138 http://archive.ubuntu.com precise-backports/restricted Translation-en [14 B]
Get:139 http://archive.ubuntu.com precise-backports/universe Translation-en [31.6 kB]
Get:140 http://archive.ubuntu.com precise-security/main Translation-en [179 kB]
Get:141 http://archive.ubuntu.com precise-security/multiverse Translation-en [1,299 B]
Get:142 http://archive.ubuntu.com precise-security/restricted Translation-en [1,253 B]
Get:143 http://archive.ubuntu.com precise-security/universe Translation-en [57.1 kB]
Err http://archive.ubuntu.com precise/restricted i386 Packages                 
  404  Not Found [IP: 91.189.91.15 80]
Err http://archive.ubuntu.com precise-updates/restricted Sources               
  404  Not Found [IP: 91.189.91.15 80]
Err http://archive.ubuntu.com precise-updates/multiverse Sources               
  404  Not Found [IP: 91.189.91.15 80]
Fetched 2,329 kB in 1min 23s (27.8 kB/s)                                       
W: &#1499;&#1513;&#1500;&#1493;&#1503; &#1489;&#1492;&#1489;&#1488;&#1514; http://archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.91.15 80] **(Hebrew part means "FAILED IN GETTING [...]")**

W: &#1499;&#1513;&#1500;&#1493;&#1503; &#1489;&#1492;&#1489;&#1488;&#1514; http://archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources  404  Not Found [IP: 91.189.91.15 80]

W: &#1499;&#1513;&#1500;&#1493;&#1503; &#1489;&#1492;&#1489;&#1488;&#1514; http://archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources  404  Not Found [IP: 91.189.91.15 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
hila@Hila:~$ 


```

---

### Post by ibjsb4 on 2014-05-17
Are you running thru a server or hooked direct the the internet?

---

### Post by xp15 on 2014-05-18
Im using a desktop pc, connected to a router with a WIFI (Wireless).
I hope I answerd good. You need more information?

Maybe I was right about my file?
> **xp15 said:**
> I cant Update, I tried many thing, I think my  /etc/apt/sources.list file is not correct (Got the idea from here: [http://askubuntu.com/questions/439264/unable-to-get-updated-package-information-apt-get-update-xubuntu-12-04](http://askubuntu.com/questions/439264/unable-to-get-updated-package-information-apt-get-update-xubuntu-12-04) , and: there: [http://ubuntuforums.org/showthread.php?t=2046145](http://ubuntuforums.org/showthread.php?t=2046145))

Here is my file content:
```
# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://releases.ubuntu.spd.co.il/ precise main restricted
deb-src http://releases.ubuntu.spd.co.il/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://releases.ubuntu.spd.co.il/ precise-updates main restricted
deb-src http://releases.ubuntu.spd.co.il/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://releases.ubuntu.spd.co.il/ precise universe
deb-src http://releases.ubuntu.spd.co.il/ precise universe
deb http://releases.ubuntu.spd.co.il/ precise-updates universe
deb-src http://releases.ubuntu.spd.co.il/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://releases.ubuntu.spd.co.il/ precise multiverse
deb-src http://releases.ubuntu.spd.co.il/ precise multiverse
deb http://releases.ubuntu.spd.co.il/ precise-updates multiverse
deb-src http://releases.ubuntu.spd.co.il/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://releases.ubuntu.spd.co.il/ precise-backports main restricted universe multiverse
deb-src http://releases.ubuntu.spd.co.il/ precise-backports main restricted universe multiverse

deb http://releases.ubuntu.spd.co.il/ precise-security main restricted
deb-src http://releases.ubuntu.spd.co.il/ precise-security main restricted
deb http://releases.ubuntu.spd.co.il/ precise-security universe
deb-src http://releases.ubuntu.spd.co.il/ precise-security universe
deb http://releases.ubuntu.spd.co.il/ precise-security multiverse
deb-src http://releases.ubuntu.spd.co.il/ precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
```

What Should I do? More solutions? I can give back output.
Please tell me what's the problem and how to fix it, so ext time I will be able to solve it.


---

### Post by xp15 on 2014-05-19
help?

---

### Post by plucky on 2014-05-20
When you switched to the main server the error was different ```
W: &#1499;&#1513;&#1500;&#1493;&#1503; &#1489;&#1492;&#1489;&#1488;&#1514; gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-backports_universe_binary-i386_Packages  Hash Sum mismatch (Hebrew part means "FAILED IN GETTING [...]")

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

You could try saving your sources.list and generating another list using [Ubuntu Sources List Generator](http://repogen.simplylinux.ch/) and see if that works.

To save your sources list use ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
``` so that if your new sources.list doesn't work,you can reuse the old list.

This is your line in your sources.list

> deb [http://releases.ubuntu.spd.co.il/](http://releases.ubuntu.spd.co.il/) precise main restricted

This is the equivalent in my sources.list > deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise main restricted

It could be your repository is set up differently, but the repositories are supposed to be mirrors of each other.

Good Luck

---

### Post by xp15 on 2014-05-20
Wait, even if the new source list works, what about all my added repository? Adding them again
about the differnce, I think it's only bacause we use different servers, no? (il vs com)

---

### Post by plucky on 2014-05-20
You could try removing all the servers from your sources.list and then adding them back one at a time and see if only one repository is causing the problem.

Also, do you require the Sources repositories to be enabled?

```
deb-src http://releases.ubuntu.spd.co.il/ precise-updates main restricted
```

Unless you require the source listings,you could disable those repositories.

Good Luck

---

### Post by deadflowr on 2014-05-20
> **xp15 said:**
> Wait, even if the new source list works, what about all my added repository? Adding them again
about the differnce, I think it's only bacause we use different servers, no? (il vs com)

3rd party repos should be in the **folder** /etc/apt/sources.list.d/
So they should not be affected in anyway by removing and replacing the **file**
/etc/apt/sources.list.
If you, however, added lines to the sources.list **file**, then you would have to re-input them.

If you adding repos with the add-apt(apt-add?)-repository command, then the added repos are in the sources.list.d folder.

But since none of the errors you have gotten have had any trouble with the 3rd party repos, they should be totally fine.

---

### Post by buzzingrobot on 2014-05-20
This might be very wide of the mark, but my sources.list, on 14.04, contains no entries like these in the OP's:```

http://archive.ubuntu.com precise/restricted i386 Packages 

```

and

```

 http://archive.ubuntu.com precise-updates/restricted Sources     


```


No entries here end with "Packages" or "Sources" .

Those entries seem to consistently produce 404 errors, indicating the target of the URL, in this case a directory on that server, either does not exist or that the server responsibile for serving its content is not responding.

Are those entries correctly formed?

The updater will not proceed if it cannot successfully update from all listed sources.

---

### Post by xp15 on 2014-05-20
> **plucky said:**
> When you switched to the main server the error was different ```
W: &#1499;&#1513;&#1500;&#1493;&#1503; &#1489;&#1492;&#1489;&#1488;&#1514; gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-backports_universe_binary-i386_Packages  Hash Sum mismatch (Hebrew part means "FAILED IN GETTING [...]")

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

You could try saving your sources.list and generating another list using [Ubuntu Sources List Generator]("http://repogen.simplylinux.ch/") and see if that works.

To save your sources list use ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
``` so that if your new sources.list doesn't work,you can reuse the old list.

This is your line in your sources.list



This is the equivalent in my sources.list 

It could be your repository is set up differently, but the repositories are supposed to be mirrors of each other.

Good Luck

I looked there, in the generator. choosing country and system is easy. What do I do in all the rest? This is too much for me ):
I really need a good explanation now.

> **plucky said:**
> You could try removing all the servers from your sources.list and then adding them back one at a time and see if only one repository is causing the problem.

Also, do you require the Sources repositories to be enabled?

```
deb-src http://releases.ubuntu.spd.co.il/ precise-updates main restricted
```

Unless you require the source listings,you could disable those repositories.

Good Luck

How would I know if I need them?

> **deadflowr said:**
> 3rd party repos should be in the **folder** /etc/apt/sources.list.d/
So they should not be affected in anyway by removing and replacing the **file**
/etc/apt/sources.list.
If you, however, added lines to the sources.list **file**, then you would have to re-input them.

If you adding repos with the add-apt(apt-add?)-repository command, then the added repos are in the sources.list.d folder.

But since none of the errors you have gotten have had any trouble with the 3rd party repos, they should be totally fine.

Thanks, I'm more relaxed now (:

> **buzzingrobot said:**
> This might be very wide of the mark, but my sources.list, on 14.04, contains no entries like these in the OP's:```

http://archive.ubuntu.com precise/restricted i386 Packages 

```

and

```

 http://archive.ubuntu.com precise-updates/restricted Sources     


```


No entries here end with "Packages" or "Sources" .

Those entries seem to consistently produce 404 errors, indicating the target of the URL, in this case a directory on that server, either does not exist or that the server responsibile for serving its content is not responding.

Are those entries correctly formed?

The updater will not proceed if it cannot successfully update from all listed sources.

OK, thanks. How do I know if they are "correctly formed?"


Thank you all. I'm just less good with this, the repos and source lists... So I need help to understand what I do, how, and why. It will help me a lot. Right now it feels like too much for me to process (Kernel Panic... (: ).

Thanks again ^^
sorry for answering after a long time. I will try better.

---

### Post by xp15 on 2014-05-21
Is there any guide which explain everything? I just dont know what im doing. Need help...

---

### Post by buzzingrobot on 2014-05-21
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

You might try editing /etc/apt/sources.list and putting a '#' at the beginning of each entry that produces an error. (The '#' means the line that follows will be ignored.)  Since the updater will just stop when it comes across an error like that -- there's no sense updating when the updater has incomplete information about what is in the repos -- sometimes this will allow the update to proceed.  That done, you can continue working to fix the problem.

'404'  is an agreed standard error code returned by a web server when the specific address sought by something -- a browser or, in this case, the updater -- either does not actually exist on the server or it does exist but can't be acccessed due to some malfunction.  In simple terms, it means "It's not here".  

If a line specifying a source in sources.list is not constructed properly, has a typo, points to a nonexistent directory on the server, i.e., is malformed, then the server will respond with a '404'. So, clearly, something is wrong with the entries producing the 404's.

As someone mentioned, this site ([http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)) offers an easy way to generate a sources.list file specific to your country. You might use it to generate a new file and then carefully overwrite you current sources.list.  That's a lot easier than spinning your wheels trying to figure out what's wrong with those entries.

---

### Post by xp15 on 2014-05-22
Got it, so I need to mark all my source with # before them, then deleting the # from one by one and checking who is causing it? It can be more than 1 right?
Thanks! (I think I got it).

The second version (Solution) is cool. The problem is that there's too much check-boxs, and I can't tell what I need ):
have you used this service once? (:

---

### Post by buzzingrobot on 2014-05-22
I'd start with only the offending lines: the lines producing the 404's.

The Repogen site lists a lot of third-party repos. Unless you know you have software from one of those sources, there is no reason to add them.  Just select the "Ubuntu" repos.  (There is no harm in selecting the "Sources" repos.  But, they are not necessary unless you want to keep the source code for everything on your system.)

---

