---
title: "Wrong or Malformed sources.list"
date: 2012-10-22
forum: General Help
---

### Post by FadeToBen on 2012-10-22
I have recently re installed Ubuntu 12.04 LTS and when I am updating.

sudo apt-get update
Ign [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise InRelease
Ign [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-updates InRelease                     
Ign [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-backports InRelease                   
Ign [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-security InRelease                    
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise Release.gpg                           
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-updates Release.gpg
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-backports Release.gpg
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg    
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-security Release.gpg
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise Release
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-updates Release              
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-backports Release                     
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-security Release                      
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise/main Sources                          
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise/restricted Sources                    
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise/universe Sources                      
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise/multiverse Sources                    
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise/main amd64 Packages                   
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise/restricted amd64 Packages             
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise/universe amd64 Packages               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise/multiverse amd64 Packages             
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise/main i386 Packages                    
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise/restricted i386 Packages              
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise/universe i386 Packages                
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise/multiverse i386 Packages              
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise/main TranslationIndex                 
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise/multiverse TranslationIndex           
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise/restricted TranslationIndex           
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise/universe TranslationIndex             
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-updates/main Sources                  
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-updates/restricted Sources            
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-updates/universe Sources              
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-updates/multiverse Sources            
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-updates/main amd64 Packages           
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-updates/restricted amd64 Packages     
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-updates/universe amd64 Packages       
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-updates/multiverse amd64 Packages     
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-updates/main i386 Packages            
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-updates/restricted i386 Packages      
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-updates/universe i386 Packages
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-updates/multiverse i386 Packages      
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-updates/main TranslationIndex         
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-updates/multiverse TranslationIndex   
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-updates/restricted TranslationIndex
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-updates/universe TranslationIndex   
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-backports/main Sources              
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-backports/restricted Sources        
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-backports/universe Sources          
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-backports/multiverse Sources        
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-backports/main amd64 Packages       
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-backports/restricted amd64 Packages 
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-backports/universe amd64 Packages   
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-backports/multiverse amd64 Packages 
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-backports/main i386 Packages        
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-backports/restricted i386 Packages  
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-backports/universe i386 Packages    
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-backports/multiverse i386 Packages  
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-backports/main TranslationIndex     
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-backports/multiverse TranslationIndex
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-backports/restricted TranslationIndex
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-backports/universe TranslationIndex 
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-security/main Sources               
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-security/restricted Sources         
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-security/universe Sources           
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-security/multiverse Sources         
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-security/main amd64 Packages        
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-security/restricted amd64 Packages  
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-security/universe amd64 Packages    
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-security/multiverse amd64 Packages
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-security/main i386 Packages         
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-security/restricted i386 Packages   
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-security/universe i386 Packages     
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-security/multiverse i386 Packages   
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-security/main TranslationIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US           
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-security/multiverse TranslationIndex
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-security/restricted TranslationIndex
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-security/universe TranslationIndex  
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise/main Translation-en                 
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise/multiverse Translation-en           
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en              
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise/restricted Translation-en
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise/universe Translation-en
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-updates/main Translation-en
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-updates/multiverse Translation-en
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-updates/restricted Translation-en
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-updates/universe Translation-en
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-backports/main Translation-en
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-backports/multiverse Translation-en
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-backports/restricted Translation-en
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-backports/universe Translation-en
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-security/main Translation-en
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-security/multiverse Translation-en
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-security/restricted Translation-en
Hit [http://ubuntu.mirror.iweb.ca](http://ubuntu.mirror.iweb.ca) precise-security/universe Translation-en
W: Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release](http://dl.google.com/linux/deb/dists/stable/Release)  Unable to find expected entry 'non-free/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)


This is what my sources.list looks like:


# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ubuntu.mirror.iweb.ca/](http://ubuntu.mirror.iweb.ca/) precise main restricted
deb-src [http://ubuntu.mirror.iweb.ca/](http://ubuntu.mirror.iweb.ca/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.mirror.iweb.ca/](http://ubuntu.mirror.iweb.ca/) precise-updates main restricted
deb-src [http://ubuntu.mirror.iweb.ca/](http://ubuntu.mirror.iweb.ca/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ubuntu.mirror.iweb.ca/](http://ubuntu.mirror.iweb.ca/) precise universe
deb-src [http://ubuntu.mirror.iweb.ca/](http://ubuntu.mirror.iweb.ca/) precise universe
deb [http://ubuntu.mirror.iweb.ca/](http://ubuntu.mirror.iweb.ca/) precise-updates universe
deb-src [http://ubuntu.mirror.iweb.ca/](http://ubuntu.mirror.iweb.ca/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.mirror.iweb.ca/](http://ubuntu.mirror.iweb.ca/) precise multiverse
deb-src [http://ubuntu.mirror.iweb.ca/](http://ubuntu.mirror.iweb.ca/) precise multiverse
deb [http://ubuntu.mirror.iweb.ca/](http://ubuntu.mirror.iweb.ca/) precise-updates multiverse
deb-src [http://ubuntu.mirror.iweb.ca/](http://ubuntu.mirror.iweb.ca/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ubuntu.mirror.iweb.ca/](http://ubuntu.mirror.iweb.ca/) precise-backports main restricted universe multiverse
deb-src [http://ubuntu.mirror.iweb.ca/](http://ubuntu.mirror.iweb.ca/) precise-backports main restricted universe multiverse

deb [http://ubuntu.mirror.iweb.ca/](http://ubuntu.mirror.iweb.ca/) precise-security main restricted
deb-src [http://ubuntu.mirror.iweb.ca/](http://ubuntu.mirror.iweb.ca/) precise-security main restricted
deb [http://ubuntu.mirror.iweb.ca/](http://ubuntu.mirror.iweb.ca/) precise-security universe
deb-src [http://ubuntu.mirror.iweb.ca/](http://ubuntu.mirror.iweb.ca/) precise-security universe
deb [http://ubuntu.mirror.iweb.ca/](http://ubuntu.mirror.iweb.ca/) precise-security multiverse
deb-src [http://ubuntu.mirror.iweb.ca/](http://ubuntu.mirror.iweb.ca/) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main






I find no obvious error, any help?

---

### Post by cortman on 2012-10-22
Check in the folder /etce/apt/sources.list.d/ for third party repository sources.lists.

---

### Post by FadeToBen on 2012-10-22
> **cortman said:**
> Check in the folder /etce/apt/sources.list.d/ for third party repository sources.lists.

I don't have the /etc/apt/sources.list.d directory at all

---

### Post by ~LoKe on 2012-10-23
> **FadeToBen said:**
> I don't have the /etc/apt/sources.list.d directory at all

What's the output of 
```
ls /etc/apt
```

---

### Post by FadeToBen on 2012-10-23
> **~LoKe said:**
> What's the output of 
```
ls /etc/apt
```

apt.conf.d     sources.list    sources.list.save  trusted.gpg   trusted.gpg.d
preferences.d  sources.list.d  trustdb.gpg        trusted.gpg~

---

### Post by ~LoKe on 2012-10-23
> **FadeToBen said:**
> apt.conf.d     sources.list    sources.list.save  trusted.gpg   trusted.gpg.d
preferences.d  sources.list.d  trustdb.gpg        trusted.gpg~

How about
```
ls /etc/apt/sources.list.d
```

---

### Post by FadeToBen on 2012-10-23
> **~LoKe said:**
> How about
```
ls /etc/apt/sources.list.d
```


oogle-chrome.list       google.list       medibuntu.list  partner.list.save
google-chrome.list.save  google.list.save  partner.list

---

### Post by ~LoKe on 2012-10-23
> **FadeToBen said:**
> oogle-chrome.list       google.list       medibuntu.list  partner.list.save
google-chrome.list.save  google.list.save  partner.list

Type this into the terminal:
```
sudo rm -R /etc/apt/sources.list.d/*
```
Then...
```
sudo apt-get update
```

---

### Post by FadeToBen on 2012-10-23
> **~LoKe said:**
> Type this into the terminal:
```
sudo rm -R /etc/apt/sources.list.d/*
```
Then...
```
sudo apt-get update
```

Worked like a charm! Thank you, can you explain what that did? I know rm is the command for remove, but unsure about -R and if the /* at the end of the path means anything?

---

### Post by ~LoKe on 2012-10-23
> **FadeToBen said:**
> Worked like a charm! Thank you, can you explain what that did? I know rm is the command for remove, but unsure about -R and if the /* at the end of the path means anything?

**rm** is indeed remove.  **-R** is recursive (removes directories and anything contained within them).  Pretty sure you had no directories in there, but there's no reason not to.  The **/*** at the end is a wildcard.  * means anything in that folder.  So, say, ```
rm -R ~/Music/*
```
That would remove ALL your albums/songs in the **~/Music** directory.

In this case...
```
rm -R /etc/apt/sources.list.d/*
```
The ***** means remove anything in **sources.list.d/**

---

### Post by FadeToBen on 2012-10-23
> **~LoKe said:**
> **rm** is indeed remove.  **-R** is recursive (removes directories and anything contained within them).  Pretty sure you had no directories in there, but there's no reason not to.  The **/*** at the end is a wildcard.  * means anything in that folder.  So, say, ```
rm -R ~/Music/*
```
That would remove ALL your albums/songs in the **~/Music** directory.

In this case...
```
rm -R /etc/apt/sources.list.d/*
```
The ***** means remove anything in **sources.list.d/**

Thank you very much for your help/guidance!!

---

### Post by ~LoKe on 2012-10-23
Any time.

---

