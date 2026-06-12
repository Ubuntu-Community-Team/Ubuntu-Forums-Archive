---
title: "Can't upgrade software using update manager gutsy"
date: 2007-11-12
forum: General Help
---

### Post by mikecomua on 2007-11-12
Hello, I have Ubuntu Gutsy and when I try to upgrade software using update manager it tries to download the files needed to check and stops on 7 of 15 and when I look down it says:```
Translation en-us Gutsy CD-ROM i686 Failed 0 bytes. Failed
``` and the it downloads the other files and says```
W: GPG error: http://download.tuxfamily.org gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E231AC7F4ECF181

``` I don't know what's wrong. Could someone help me. Thanks!

---

### Post by taurus on 2007-11-12
Can you post your /etc/apt/sources.list?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by mikecomua on 2007-11-12
```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://ua.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://ua.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://ua.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://ua.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://ua.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://ua.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://ua.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://ua.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://ua.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://ua.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://ua.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://ua.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ua.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://ua.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ gutsy universe multiverse restricted main
deb-src http://archive.ubuntu.com/ubuntu/ gutsy universe main multiverse restricted #Added by software-properties
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

---

### Post by taurus on 2007-11-12
Doesn't look like you have all the repos available.  Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line to comment out the cdrom so it won't ask you to insert a CD into the drive from now on.  Then, remove the # in front of all the lines that start with **deb** and **deb-src**.  Save it and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by mikecomua on 2007-11-12
Here's what it gave me```
mike@mike-ubuntu-laptop:~$ sudo apt-get update
6% [Working]
Get:1 http://archive.ubuntu.com gutsy Release.gpg [191B]                       
Ign http://archive.ubuntu.com gutsy/universe Translation-en_US                 
Get:2 http://archive.canonical.com gutsy Release.gpg [191B]                    
Ign http://archive.canonical.com gutsy/partner Translation-en_US
Ign http://archive.ubuntu.com gutsy/multiverse Translation-en_US
Ign http://archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://archive.ubuntu.com gutsy/main Translation-en_US
Hit http://archive.ubuntu.com gutsy Release    
Hit http://archive.canonical.com gutsy Release 
Hit http://archive.ubuntu.com gutsy/universe Packages
Ign http://archive.canonical.com gutsy/partner Packages
Hit http://archive.ubuntu.com gutsy/multiverse Packages
Hit http://archive.ubuntu.com gutsy/restricted Packages
Hit http://archive.ubuntu.com gutsy/main Packages
Ign http://archive.canonical.com gutsy/partner Sources
Hit http://archive.ubuntu.com gutsy/universe Sources
Hit http://archive.ubuntu.com gutsy/main Sources
Hit http://archive.ubuntu.com gutsy/multiverse Sources
Hit http://archive.ubuntu.com gutsy/restricted Sources
Hit http://archive.canonical.com gutsy/partner Packages
Hit http://archive.canonical.com gutsy/partner Sources
Fetched 2B in 20s (0B/s)
Reading package lists... Done
W: Duplicate sources.list entry http://archive.canonical.com gutsy/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_gutsy_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
mike@mike-ubuntu-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mike@mike-ubuntu-laptop:~$ 


```
BTW, why gksudo?

---

### Post by taurus on 2007-11-12
Just run the first command again.

Gksudo is a GUI of sudo.

---

### Post by mikecomua on 2007-11-12
```
mike@mike-ubuntu-laptop:~$ sudo apt-get update
Get:1 http://archive.ubuntu.com gutsy Release.gpg [191B]                      
Ign http://archive.ubuntu.com gutsy/universe Translation-en_US                
Ign http://archive.ubuntu.com gutsy/multiverse Translation-en_US
Get:2 http://archive.canonical.com gutsy Release.gpg [191B]
Ign http://archive.canonical.com gutsy/partner Translation-en_US
Ign http://archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://archive.ubuntu.com gutsy/main Translation-en_US
Hit http://archive.ubuntu.com gutsy Release    
Hit http://archive.canonical.com gutsy Release 
Hit http://archive.ubuntu.com gutsy/universe Packages
Ign http://archive.canonical.com gutsy/partner Packages
Hit http://archive.ubuntu.com gutsy/multiverse Packages
Hit http://archive.ubuntu.com gutsy/restricted Packages
Hit http://archive.ubuntu.com gutsy/main Packages
Ign http://archive.canonical.com gutsy/partner Sources
Hit http://archive.ubuntu.com gutsy/universe Sources
Hit http://archive.ubuntu.com gutsy/main Sources
Hit http://archive.ubuntu.com gutsy/multiverse Sources
Hit http://archive.ubuntu.com gutsy/restricted Sources
Hit http://archive.canonical.com gutsy/partner Packages
Hit http://archive.canonical.com gutsy/partner Sources
Fetched 2B in 20s (0B/s)
Reading package lists... Done

```

---

