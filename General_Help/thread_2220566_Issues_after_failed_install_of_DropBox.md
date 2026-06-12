---
title: "Issues after failed install of DropBox"
date: 2014-04-28
forum: General Help
---

### Post by Madman1978 on 2014-04-28
I had a failed attempt - broken package with DropBox.  

I had an issue with the updater. - Solved that issue Thank you Forums! 

I also followed all the suggestions in another thread on how to remove and clean up the mess that failed install- Again thank you Forums 



However, several problems still exist.  I have lost Software Center and I have no text Editor - The system is using wine to open notepad...


I am at a stand still.  Everything remains stable but just those issues.  
Thank you in advance for any help!

---

### Post by bapoumba on 2014-04-28
Would you please post the output to
```
sudo apt-get update
sudo apt-get upgrade
cat /etc/sources.list
ls /etc/apt/sources.list.d
```

---

### Post by Frogs Hair on 2014-04-28
Try the following commands one at a time in the terminal and report any errors . If the applications open attempt it with the launcher icons. The software center will display normal errors when launched from the terminal.

```
gedit
```

```
software-center
```

---

### Post by Madman1978 on 2014-04-28
> **bapoumba said:**
> Would you please post the output to
```
sudo apt-get update
sudo apt-get upgrade
cat /etc/sources.list
ls /etc/apt/sources.list.d
```


```
sudo apt-get update
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                      
Ign [http://dl.google.com](http://dl.google.com) stable InRelease      
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                    
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg    
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [58.5 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                          
Hit [http://dl.google.com](http://dl.google.com) stable Release                                      
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg [933 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release [58.5 kB]
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [14 B]       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release                      
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                       
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [4,022 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [14 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                 
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [14 B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages [7,730 B] 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                     
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages [14 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main amd64 Packages                  
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages [2,119 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted amd64 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe amd64 Packages                
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages [14 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse amd64 Packages     
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [7,736 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [14 B]
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [2,119 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages               
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [14 B]
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [2,748 B]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [8,132 B]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [1,790 B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [14 B]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main amd64 Packages [18.2 kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [14 B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe amd64 Packages [6,523 B]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [6,362 B]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [16.9 kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en_US
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [14 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en_US
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [6,549 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en_US
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [6,386 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translat
```


```
cat /etc/sources.list
cat: /etc/sources.list: No such file or directory
```


```
ls /etc/apt/sources.list.d
ehoover-compholio-saucy.list       mqchael-pipelight-saucy.list
ehoover-compholio-saucy.list.save  mqchael-pipelight-saucy.list.save
google-chrome.list                 pipelight-stable-saucy.list
google-chrome.list.distUpgrade     pipelight-stable-saucy.list.distUpgrade
google-chrome.list.save            pipelight-stable-saucy.list.save
google-earth.list                  playonlinux.list
google-earth.list.distUpgrade      playonlinux.list.distUpgrade
google-earth.list.save             playonlinux.list.save
```




-Thank you for your Assistance

---

### Post by Madman1978 on 2014-04-28
> **Frogs Hair said:**
> Try the following commands one at a time in the terminal and report any errors . If the applications open attempt it with the launcher icons. The software center will display normal errors when launched from the terminal.

```
gedit
```

```
software-center
```

Neither were installed? 

What thats says to me is that the Drop Box install removed them ?

Installing them now.

---

### Post by Frogs Hair on 2014-04-28
I have installed nautilus-dropbox on both my computers, but have never removed it is possible there are some shared dependencies that were removed with dropbox.

---

### Post by Madman1978 on 2014-04-28
I think you missing the point 

I attempt to install drop box and it failed.  Which left me with some broken issues.  I had to fix the broken package.  Which i have but I had lost Software Center and gedit.  I cant understand how I lost those and why would they be removed?

---

### Post by Madman1978 on 2014-04-28
Finding more and more things that have been chanced or removed by this screwed up program!  I really didnt need drop box any way

---

### Post by bapoumba on 2014-04-29
```
cat /etc/sources.list
cat: /etc/sources.list: No such file or directory
```

I am sorry, made a typo there. should be :
```
cat /etc/apt/sources.list
```

Please run the **sudo apt-get update** once more, and run **sudo apt-get upgrade** after, and please post the output.

If you are using the regular ubuntu flavor, please run :
```
apt-cache policy ubuntu-desktop
```

---

### Post by Frogs Hair on 2014-04-29
See the above post . The method used to fix the broken packages may account for the missing packages .

---

### Post by Madman1978 on 2014-04-29
> **bapoumba said:**
> ```
cat /etc/sources.list
cat: /etc/sources.list: No such file or directory
```

I am sorry, made a typo there. should be :
```
cat /etc/apt/sources.list
```

Please run the **sudo apt-get update** once more, and run **sudo apt-get upgrade** after, and please post the output.

If you are using the regular ubuntu flavor, please run :
```
apt-cache policy ubuntu-desktop
```

```

# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)]/ quantal main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe main multiverse restricted #Added by software-properties


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe main multiverse restricted #Added by software-properties


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse #Added by software-properties


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe main multiverse restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
# deb [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner
# deb-src [http://archive.canonical.com/](http://archive.canonical.com/) saucy partner

```







```
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                      
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                    
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                   
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg [933 B] 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release [58.5 kB]            
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]         
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [58.5 kB]             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main amd64 Packages                    
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted amd64 Packages
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [14 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [4,953 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [14 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en       
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [4,235 B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [14 B]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [8,966 B]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [1,790 B]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [14 B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages [9,570 B]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main amd64 Packages [19.9 kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [14 B]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe amd64 Packages [9,387 B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages [14 B]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [6,362 B]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [18.6 kB]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages [3,215 B]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [14 B]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [9,408 B]
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages [14 B]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [6,386 B]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [9,592 B]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en [10.2 kB]
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [14 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [3,226 B]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en [5,687 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources                
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [14 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted amd64 Packages
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en [5,497 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe amd64 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en [2,077 B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en_US
Fetched 258 kB in 4s (54.3 kB/s)
Reading package lists... Done
```








```
Installed: (none)
  Candidate: 1.325
  Version table:
     1.325 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
```

---

### Post by bapoumba on 2014-04-29
Please install ubuntu-desktop :
```
sudo apt-get install ubuntu-desktop
```

---

### Post by Madman1978 on 2014-04-29
ubuntu-desktop:
  Installed: 1.325
  Candidate: 1.325
  Version table:
 *** 1.325 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
        100 /var/lib/dpkg/status


I think it is back to normal?  

Has this happened before? 
Is there something i did not do to cause this issue to happen?


And again - THANK YOU!

---

### Post by bapoumba on 2014-04-29
> **Madman1978 said:**
> ubuntu-desktop:
  Installed: 1.325
  Candidate: 1.325
  Version table:
 *** 1.325 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
        100 /var/lib/dpkg/status


I think it is back to normal?  

Has this happened before? 
Is there something i did not do to cause this issue to happen?


And again - THANK YOU!

To make sure everything is back to normal and stays that way, please disable all your saucy ppa, namely :
```
ehoover-compholio-saucy.list       
ehoover-compholio-saucy.list.save  
mqchael-pipelight-saucy.list
mqchael-pipelight-saucy.list.save
pipelight-stable-saucy.list
pipelight-stable-saucy.list.distUpgrade
pipelight-stable-saucy.list.save
```

Most probably, you did the upgrade without disabling them OR you activated the wrong ones on Trusty. Some play nice on upgrades, some do not.

ubuntu-desktop is a meta-package, that means it does not contain any executable but it depends on many others. In this case, the ubuntu desktop environment and a lot of associated applications (such as gedit : [http://packages.ubuntu.com/trusty/ubuntu-desktop](http://packages.ubuntu.com/trusty/ubuntu-desktop)).

If at some point, to satisfy dependencies when installing something (and I bet this was not dropbox, but my crystal ball is failing me here) you said yes to uninstall ubuntu-desktop, then said yes to auto-remove packages that were automatically installed (all the ones that ubuntu-desktop depends on), then they got uninstalled.

[https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

---

### Post by Madman1978 on 2014-04-29
Thank yiou so much all appears to be smooth sailing for right now

---

### Post by bapoumba on 2014-04-30
If your issue is solved, please mark your thread as such, in Thread Tools, thanks!

---

