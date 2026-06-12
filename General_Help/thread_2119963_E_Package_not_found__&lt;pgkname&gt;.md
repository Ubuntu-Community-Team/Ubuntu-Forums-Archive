---
title: "E: Package not found  &lt;pgkname&gt;"
date: 2013-02-25
forum: General Help
---

### Post by billiam2296 on 2013-02-25
It appears that whenever I try to install any package, I recieve the error E: Package not found  <pgkname>

Currently I am trying to install flash, so I type in :

sudo apt-get install flashplugin-nonfree

I've tried other versions that I've found online besides flashplugin-nonfree, with the same results.  I suspect this has something to do with sources.list

I should mention that I have been having this problem for a little while, and (stupidly) copied the sources.list from my other computer (Ubuntu x64) without remembering that the computer I did the target computer was actually not Ubuntu but rather Lubuntu for PowerPC.  I seem to recall that sources.list only had one line in it before I overwrote it, but unfortunately I didn't save a copy (sorry!).  

Here is the output from sudo apt-get update: 

```
william@ubuntuGSALIB5:~$ sudo apt-get update
[sudo] password for william: 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg                   
Get:1 [http://repository.spotify.com](http://repository.spotify.com) stable InRelease [2,979 B]                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg     
Ign [http://repository.spotify.com](http://repository.spotify.com) stable InRelease   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free TranslationIndex             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main powerpc Packages          
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main powerpc Packages                 
  404  Not Found [IP: 91.189.91.13 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted powerpc Packages    
  404  Not Found [IP: 91.189.91.13 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe powerpc Packages      
  404  Not Found [IP: 91.189.91.13 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse powerpc Packages    
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted powerpc Packages           
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe powerpc Packages   
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse powerpc Packages 
  404  Not Found [IP: 91.189.91.13 80]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main powerpc Packages           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main powerpc Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted powerpc Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe powerpc Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse powerpc Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main powerpc Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted powerpc Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe powerpc Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse powerpc Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://repository.spotify.com](http://repository.spotify.com) stable/non-free powerpc Packages   
  404  Not Found
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
Fetched 2,979 B in 2s (1,215 B/s)
W: GPG error: [http://repository.spotify.com](http://repository.spotify.com) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 082CCEDF94558F59
W: Failed to fetch [http://repository.spotify.com/dists/stable/non-free/binary-powerpc/Packages](http://repository.spotify.com/dists/stable/non-free/binary-powerpc/Packages)  404  Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/main/binary-powerpc/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/main/binary-powerpc/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-powerpc/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-powerpc/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/binary-powerpc/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/binary-powerpc/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-powerpc/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-powerpc/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-powerpc/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-powerpc/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-powerpc/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-powerpc/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-powerpc/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-powerpc/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-powerpc/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-powerpc/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-powerpc/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-powerpc/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-powerpc/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-powerpc/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-powerpc/Packages)  404  Not Found [IP: 91.189.91.13 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
```






```
william@ubuntuGSALIB5:/etc/apt$ cat sources.list
#deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/main/binary-i386/

#deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/restricted/binary-i386/
#deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main


deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
```

For cat sources.list (in the appropriate directory) I get this:

---

### Post by schragge on 2013-02-25
Weird. apt is trying to get updates for powerpc architecture, but the comments in sources.list say both amd64 and i386. What kind of machine is this?

What does *dpkg --print-architecture* show?

AFAIK, for powerpc your *sources.list* should point to *ports.ubuntu.com*

---

### Post by raja.genupula on 2013-02-25
you'd better re-generate your source list.
repogen.simplylinux.ch/

---

### Post by cortman on 2013-02-25
Schragge brings up some good points.
If I were you, I would use the [Sources List Generator]("http://repogen.simplylinux.ch/") to make a new sources.list.
But first you must specify what architecture you have. Are you using this on an old PPC Mac?
FYI, for Ubuntu you want to run

```
apt-get install flashplugin-installer
```

rather than flashplugin-nonfree. That's a Debian package.

---

### Post by billiam2296 on 2013-02-25
Thanks for all the suggestion... before I try them and make some (another :confused:) horrible mistake, I will follow Cortman's advice.  

> **cortman said:**
> Schragge brings up some good points.
But first you must specify what architecture you have. Are you using this on an old PPC Mac?

Yes, I am on a PPC Mac (iBook G4).  

lsb_release produces the output:
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04 LTS
Release:    12.04
Codename:    precise

It's LUBUNTU and I installed it just yesterday (downloaded yesterday, too).  

I don't know if it's relevant, but when I installed it, when it was at the installing software step (I used the special install disc) it failed twice so I just skipped it.  When I got it up and running, there was no GUI, so I had to install that manually from the disc.

---

### Post by schragge on 2013-02-25
Well, your sources.list is completely wrong then.
As a starting point, replace it with 
```

deb http://ports.ubuntu.com/ precise main restricted
deb-src http://ports.ubuntu.com/ precise main restricted

deb http://ports.ubuntu.com/ precise-updates main restricted
deb-src http://ports.ubuntu.com/ precise-updates main restricted

deb http://ports.ubuntu.com/ precise universe
deb-src http://us.archive.ubuntu.com/ precise universe
deb http://ports.ubuntu.com/ precise-updates universe
deb-src http://ports.ubuntu.com/ precise-updates universe

deb http://ports.ubuntu.com/ precise multiverse
deb-src http://ports.ubuntu.com/ precise multiverse
deb http://ports.ubuntu.com/ precise-updates multiverse
deb-src http://ports.ubuntu.com/ precise-updates multiverse

deb http://ports.ubuntu.com/ precise-backports main restricted universe multiverse
deb-src http://ports.ubuntu.com/ precise-backports main restricted universe multiverse

deb http://ports.ubuntu.com/ precise-security main restricted
deb-src http://ports.ubuntu.com/ precise-security main restricted
deb http://security.ubuntu.com/ precise-security universe
deb-src http://ports.ubuntu.com/ precise-security universe
deb http://ports.ubuntu.com/ precise-security multiverse
deb-src http://ports.ubuntu.com/ precise-security multiverse

```
and try to *sudo apt-get update* again. Then you can generate new sources.list as suggested above, or extend this gradually, checking each time after adding a new repository if it still works.

---

### Post by cortman on 2013-02-25
> **billiam2296 said:**
> Thanks for all the suggestion... before I try them and make some (another :confused:) horrible mistake, I will follow Cortman's advice.  



Yes, I am on a PPC Mac (iBook G4).  

lsb_release produces the output:
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04 LTS
Release:    12.04
Codename:    precise

It's LUBUNTU and I installed it just yesterday (downloaded yesterday, too).  

I don't know if it's relevant, but when I installed it, when it was at the installing software step (I used the special install disc) it failed twice so I just skipped it.  When I got it up and running, there was no GUI, so I had to install that manually from the disc.

Create a new sources.list file using the link I gave, and then run

```
sudo apt-get update
```

dpkg sets the architecture at the installation, so you should be fine after that. Either delete the old sources.list, or else rename it sources.list.old (although as messed up as it is I'd just delete it).
Good luck!

---

### Post by billiam2296 on 2013-02-25
I found the original sources.list stored in sources.list.save 

It 'helped', as I no longer get E: Package not found, but now I get this output:

```

william@ubuntuGSALIB5:~/Documents$ sudo apt-get install flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-installer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'flashplugin-installer' has no installation candidate


```

And, here is the contents of the new sources.list I found
```

# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main


deb http://ports.ubuntu.com/ubuntu-ports/ precise main universe restricted
deb http://repository.spotify.com stable non-free

```

When I update, the output still isn't perfect, as it still has some errors: 
```

william@ubuntuGSALIB5:~$ sudo apt-get update
[sudo] password for william: 
Ign http://archive.canonical.com precise InRelease                             
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://archive.canonical.com precise Release                               
Ign http://us.archive.ubuntu.com precise InRelease                             
Ign http://us.archive.ubuntu.com precise-updates InRelease                     
Ign http://us.archive.ubuntu.com precise-backports InRelease                   
Hit http://us.archive.ubuntu.com precise Release.gpg                           
Hit http://us.archive.ubuntu.com precise-updates Release.gpg                   
Get:1 http://repository.spotify.com stable InRelease [2,979 B]                 
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://us.archive.ubuntu.com precise Release                               
Hit http://us.archive.ubuntu.com precise-updates Release                       
Hit http://us.archive.ubuntu.com precise-backports Release                     
Ign http://repository.spotify.com stable InRelease                             
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://archive.canonical.com precise/partner powerpc Packages              
Ign http://repository.spotify.com stable/non-free TranslationIndex             
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Hit http://us.archive.ubuntu.com precise-updates/main Sources                  
Hit http://us.archive.ubuntu.com precise-updates/restricted Sources            
Hit http://us.archive.ubuntu.com precise-updates/universe Sources              
Hit http://us.archive.ubuntu.com precise-updates/multiverse Sources            
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://us.archive.ubuntu.com precise-backports/main Sources                
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://us.archive.ubuntu.com precise-backports/universe Sources            
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en     
Err http://us.archive.ubuntu.com precise/main powerpc Packages                 
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com precise/restricted powerpc Packages           
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com precise/universe powerpc Packages             
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com precise/multiverse powerpc Packages           
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com precise-updates/main powerpc Packages         
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com precise-updates/restricted powerpc Packages   
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com precise-updates/universe powerpc Packages     
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com precise-updates/multiverse powerpc Packages   
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com precise-backports/main powerpc Packages       
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com precise-backports/restricted powerpc Packages 
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com precise-backports/universe powerpc Packages   
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com precise-backports/multiverse powerpc Packages 
  404  Not Found [IP: 91.189.91.13 80]
Err http://repository.spotify.com stable/non-free powerpc Packages             
  404  Not Found
Ign http://repository.spotify.com stable/non-free Translation-en_US            
Ign http://ports.ubuntu.com precise InRelease                                  
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://security.ubuntu.com precise-security InRelease                      
Ign http://repository.spotify.com stable/non-free Translation-en               
Hit http://ports.ubuntu.com precise Release.gpg                                
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://security.ubuntu.com precise-security Release.gpg          
Hit http://extras.ubuntu.com precise Release                                   
Hit http://security.ubuntu.com precise-security Release                        
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://extras.ubuntu.com precise/main powerpc Packages           
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://security.ubuntu.com precise-security/main Sources                   
Hit http://security.ubuntu.com precise-security/restricted Sources             
Hit http://security.ubuntu.com precise-security/universe Sources               
Hit http://security.ubuntu.com precise-security/multiverse Sources             
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://ports.ubuntu.com precise Release                                    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Hit http://ports.ubuntu.com precise/main powerpc Packages                      
Hit http://security.ubuntu.com precise-security/main Translation-en  
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Ign http://extras.ubuntu.com precise/main Translation-en                       
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://ports.ubuntu.com precise/universe powerpc Packages        
Hit http://ports.ubuntu.com precise/restricted powerpc Packages      
Hit http://ports.ubuntu.com precise/main TranslationIndex            
Hit http://security.ubuntu.com precise-security/universe Translation-en
Err http://security.ubuntu.com precise-security/main powerpc Packages
  404  Not Found [IP: 91.189.92.200 80]
Err http://security.ubuntu.com precise-security/restricted powerpc Packages
  404  Not Found [IP: 91.189.92.200 80]
Err http://security.ubuntu.com precise-security/universe powerpc Packages
  404  Not Found [IP: 91.189.92.200 80]
Err http://security.ubuntu.com precise-security/multiverse powerpc Packages
  404  Not Found [IP: 91.189.92.200 80]
Hit http://ports.ubuntu.com precise/restricted TranslationIndex                
Hit http://ports.ubuntu.com precise/universe TranslationIndex                  
Hit http://ports.ubuntu.com precise/main Translation-en                        
Hit http://ports.ubuntu.com precise/restricted Translation-en                  
Hit http://ports.ubuntu.com precise/universe Translation-en                    
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://archive.canonical.com precise/partner Translation-en
Fetched 2,979 B in 12s (243 B/s)
W: GPG error: http://repository.spotify.com stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 082CCEDF94558F59
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-powerpc/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-powerpc/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-powerpc/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-powerpc/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://repository.spotify.com/dists/stable/non-free/binary-powerpc/Packages  404  Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-powerpc/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-powerpc/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-powerpc/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-powerpc/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-powerpc/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-powerpc/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-powerpc/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-powerpc/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/main/binary-powerpc/Packages  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-powerpc/Packages  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/universe/binary-powerpc/Packages  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-powerpc/Packages  404  Not Found [IP: 91.189.92.200 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.


```

And now I don't have the problem with EVERY package I try to install like I did before, as I just was finally able to install JAVA.  :p

---

### Post by cortman on 2013-02-25
Hm, try changing the repository mirror? Per instructions [here]("http://askubuntu.com/questions/37753/how-can-i-get-apt-to-use-a-mirror-close-to-me-or-choose-a-faster-mirror"), second answer.
As soon as that updates fine you should be able to install flash.

---

### Post by schragge on 2013-02-25
@billiam2296
You're still don't getting any updates. As I said before, *us.archive.ubuntu.com* is **wrong**, it doesn't host packages for PowerPC. Instead, try with *ports.ubuntu.com* from the example in my previous post.

[highlight]Update.[/highlight]
Sorry, I didn't noticed *ports.ubuntu.com* line in your new sources.list. So, you're getting **some** updates, but not all of them. I'd still suggest you replace this source.list with the one from [post=12529955]my post above[/post].

---

