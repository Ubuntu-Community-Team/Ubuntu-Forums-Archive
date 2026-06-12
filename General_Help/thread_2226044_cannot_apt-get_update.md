---
title: "cannot apt-get update"
date: 2014-05-24
forum: General Help
---

### Post by Spidey1980 on 2014-05-24
I am using Xubuntu Trusty LTS on my duel boot system with windows.

I am getting a wholle bunch of "Failed to fetch ([http://.](http://.)..) Unable to find expected entry 'main/binary-i38/Packages' in Release file (Wrong sources.list entry or malformed file)

Here is the output from the console:
```
spidey@Spidey-Satellite-A505:~/Desktop$ sudo apt-get update
Ign http://us.archive.ubuntu.com trusty InRelease
Ign http://us.archive.ubuntu.com trusty-updates InRelease                      
Ign http://us.archive.ubuntu.com trusty-backports InRelease                    
Ign http://security.ubuntu.com trusty-security InRelease                       
Hit http://deb.playonlinux.com maverick InRelease                              
Ign http://us.archive.ubuntu.com trusty-proposed InRelease                     
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security Release.gpg                     
Get:1 http://us.archive.ubuntu.com trusty-updates Release.gpg [933 B]          
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:2 http://us.archive.ubuntu.com trusty-backports Release.gpg [933 B]        
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://security.ubuntu.com trusty-security Release                         
Get:3 http://us.archive.ubuntu.com trusty-proposed Release.gpg [933 B]         
Hit http://deb.playonlinux.com maverick/main amd64 Packages                    
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://extras.ubuntu.com trusty Release                                    
Get:4 http://us.archive.ubuntu.com trusty-updates Release [58.5 kB]            
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Get:5 http://ppa.launchpad.net trusty Release.gpg [316 B]                      
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Get:6 http://us.archive.ubuntu.com trusty-backports Release [58.6 kB]          
Hit http://ppa.launchpad.net trusty Release                                   
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Get:7 http://us.archive.ubuntu.com trusty-proposed Release [58.5 kB]           
Get:8 http://ppa.launchpad.net trusty Release [14.0 kB]                       
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages       
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages        
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Get:9 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [98.0 kB]
Get:10 http://ppa.launchpad.net trusty/main amd64 Packages [32.3 kB]
Get:11 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [14 B]
Get:12 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [66.8 kB]
Get:13 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [7,089 B]
Get:14 http://us.archive.ubuntu.com trusty-backports/main amd64 Packages [14 B]
Get:15 http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages [14 B]
Get:16 http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages [3,603 B]
Get:17 http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages [619 B]
Get:18 http://us.archive.ubuntu.com trusty-proposed/universe amd64 Packages [20.6 kB]
Get:19 http://us.archive.ubuntu.com trusty-proposed/restricted amd64 Packages [14 B]
Get:20 http://us.archive.ubuntu.com trusty-proposed/multiverse amd64 Packages [14 B]
Get:21 http://us.archive.ubuntu.com trusty-proposed/main amd64 Packages [52.7 kB]
Fetched 475 kB in 2s (208 kB/s) 
W: Failed to fetch http://deb.playonlinux.com/dists/maverick/InRelease  Unable to find expected entry 'main/binary-i38/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/Release  Unable to find expected entry 'main/binary-i38/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/Release  Unable to find expected entry 'main/binary-i38/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release  Unable to find expected entry 'main/binary-i38/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/Release  Unable to find expected entry 'main/binary-i38/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/Release  Unable to find expected entry 'main/binary-i38/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-proposed/Release  Unable to find expected entry 'universe/binary-i38/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/trusty/Release  Unable to find expected entry 'main/binary-i38/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/dists/trusty/Release  Unable to find expected entry 'main/binary-i38/Packages' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.


```

Obviously the "i38" should be "i386" however theres is no suc h entries in my sources.list for the update to even try those sources:
```
# deb cdrom:[Xubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.1)]/ quantal main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu quantal partner
# deb-src http://archive.canonical.com/ubuntu quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
# deb-src http://extras.ubuntu.com/ubuntu raring main
deb http://us.archive.ubuntu.com/ubuntu/ trusty-proposed universe restricted multiverse main


```

Is there something that I am missing? (oh and I have no gedit either, I have to use mousepad to edit but I am unsure if that will save it, I have not even tried to manually edit my sources.list)

---

### Post by pqwoerituytrueiwoq on 2014-05-24
does [FONT=courier new]dpkg --print-architecture[/FONT] give you i386?

---

### Post by llamabr on 2014-05-25
Also maybe we can look at your /etc/apt/sources.list

---

### Post by LastDino on 2014-05-25
Mousepad is not half bad, in fact; I use it instead of gedit and leafpad. From looks of it, your resource list seems to be broken, reply to llamabr's post would be helpfu, but till then you might want to consider removing CDrom option and also check your PPA's by browsing through graphical software update manager.

---

### Post by Mischa_Deden on 2014-10-07
> **pqwoerituytrueiwoq said:**
> does [FONT=courier new]dpkg --print-architecture[/FONT] give you i386?
  
I had the same problem. 
First check your normal architecture with [FONT=courier new]dpkg --print-architecture [/FONT]I have a 64 bits machine so the anwers is [FONT=courier new]amd64[/FONT]

[FONT=courier new][/FONT]After that run [FONT=courier new]dpkg --print-foreign-architectures [/FONT]That showed it :D 
[FONT=courier new]i386
i38[/FONT]

So I found the error. I don't know how this happened  but I think when adding 32bits libs to my system I have made a type ;)

And the enter [FONT=courier new]dpkg --remove-architecture i38[/FONT] to remove the wrong entry

Et voila, problem solved 

Good luck

---

