---
title: "Software Sources problem"
date: 2007-12-15
forum: General Help
---

### Post by MONODA on 2007-12-15
Hi I only have the medibuntu and gutsy and origina gutsy keys added to my repositories list. Whenever I try to reload, I get an error telling me that there was a 404 error. Doesnt that mean that the key isnt correct? Could anyone provide me with the correct medibuntu and original repositories? Thank you.

---

### Post by forestpixie on 2007-12-15
you can get a new set from here - [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

you'll need to edit your original list and delete all that's there and then paste in the list that gets produced.

have you got a separate medibuntu list? it would be in this directory probably
/etc/apt/sources.list.d

if so do the same for that list

medibuntu repos are here - follow the instructions

[https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)

---

### Post by MONODA on 2007-12-15
Thanks that was really helpful.

---

### Post by MONODA on 2007-12-15
Wait im still getting some problems. this is what I get when I type sudo apt-get update:
> Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]
Get:2 [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) gutsy Release.gpg [191B]                  
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]          
Ign [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) gutsy/main Translation-en_US               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Ign [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) gutsy/restricted Translation-en_US  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release                    
  
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release [2723B]          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release                                
Ign [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) gutsy/universe Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                          
Ign [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) gutsy/multiverse Translation-en_US            
Get:5 [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) gutsy-updates Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages                      
Ign [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) gutsy-updates/main Translation-en_US          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                          
Ign [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages                      
Ign [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) gutsy-updates/universe Translation-en_US      
Ign [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US    
Hit [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) gutsy Release
Hit [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) gutsy-updates Release
Hit [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) gutsy/main Packages
Hit [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) gutsy/universe Packages
Hit [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) gutsy-updates/multiverse Packages
Fetched 2915B in 21s (136B/s)
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures were invalid: BADSIG 2EBC26B60C5A2783 Medibuntu Packaging Team <admin@lists.medibuntu.org>
W: You may want to run apt-get update to correct these problems

and in my software sources I can only see the medibuntu repository in third party software and I cant see the ubuntu one.

---

### Post by forestpixie on 2007-12-15
did you do this after you added the medibuntu sources, because it looks like you didn't

> wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

if you didn't , do it now and try the apt-get update command again

if however you did do it, can you post these

```
cat /etc/apt/sources.list
```
```
cat /etc/apt/sources.list.d/medibuntu.list
```

---

### Post by MONODA on 2007-12-15
> deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://lb.archive.ubuntu.com/ubuntu/](http://lb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed universe main multiverse restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

> ## Medibuntu - Ubuntu 7.10 "gutsy gibbon"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

I did this after adding medibuntu.

---

### Post by forestpixie on 2007-12-15
did you actually do this bit of my first post?
> 
you'll need to edit your original list and delete all that's there and then paste in the list that gets produced

open a terminal, do this
```
gksudo gedit /etc/apt/sources.list
```

once it's open, select all and delete - paste this in

> # Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://lb.archive.ubuntu.com/ubuntu](http://lb.archive.ubuntu.com/ubuntu) gutsy main restricted 
deb [http://lb.archive.ubuntu.com/ubuntu](http://lb.archive.ubuntu.com/ubuntu) gutsy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://lb.archive.ubuntu.com/ubuntu](http://lb.archive.ubuntu.com/ubuntu) gutsy universe multiverse 
deb [http://lb.archive.ubuntu.com/ubuntu](http://lb.archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe multiverse

save and close - then in terminal do these once more

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by MONODA on 2007-12-15
yes I did do that but I will do it again. When I run, > wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update I get > OK
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory
 What does that mean?

---

### Post by g2g591 on 2007-12-15
it means apt is probabily running downloading updates in the background. do pidof apt-get then do sudo kill whatever number the last command put out') then try sudo apt-get update

---

