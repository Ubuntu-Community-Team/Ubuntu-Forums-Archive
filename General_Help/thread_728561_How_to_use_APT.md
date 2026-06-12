---
title: "How to use APT?"
date: 2008-03-18
forum: General Help
---

### Post by sparksandtabs on 2008-03-18
I am new to Ubuntu, I know how to get around, and know UNIX commands, but I cannot get the Applications manager to work. I started by trying to use the visual one, but every time I open it to install a new package I get a message saying "The list of applications is not availible" So....I click refresh and it says it loads it then I try again and the whole thing happens all over again. After this I switch to command line "sudo apt-get install [filename]" etc and all the other fun commands, But on the command line I even get a message saying  "Unable to find package [filename]"

I have the latest version 7.10. Any help would be appreciated!

Thanks,
John

---

### Post by myusername on 2008-03-18
well for starters make sure your connected to the internet

---

### Post by artificialive on 2008-03-19
Perhaps u can try to run 

```
sudo apt-get update 
``` to refresh your apt's cache.  Then, run ```
sudo apt-get upgrade
``` to launch the upgrade of the cache.

---

### Post by aysiu on 2008-03-19
Can you paste the output of this [terminal](http://www.psychocats.net/ubuntu/terminal) command? ```
cat /etc/apt/sources.list
```

---

### Post by sparksandtabs on 2008-03-19
Obviously I need to be on the internet....I did post this thread didn't I? :P

output of the terminal command( given by aysiu ):
```
john@john-desktop:/$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
john@john-desktop:/$ 

```

This is the output of the commands given by artificialive:
```
john@john-desktop:/$ sudo apt-get update
[sudo] password for john:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Reading package lists... Done
john@john-desktop:/$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
john@john-desktop:/$ sudo apt-get install kbounce
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kbounce
john@john-desktop:/$ 

```

---

### Post by aysiu on 2008-03-19
First of all, you would think everyone who posts on an online forum would be connected to the internet, but such is not always the case. Sometimes people have Windows computers they use to connect and their Ubuntu is disconnected, or they use a public terminal to post problems (as at an internet cafe or a library).

Looking at your sources.list file, it appears you have only one software repository source enabled--the Ubuntu CD-ROM, which has virtually no packages on it.

The *#* at the beginning of the line tells APT "Hey, anything after this symbol until the end of the line... act as if it doesn't exist."

So go to System > Administration > Software Sources and check all the boxes. When prompted to Reload, do it.

---

### Post by sparksandtabs on 2008-03-19
I am aware of the internet thing I was trying to point out the whole irony thing.....

And changing the software source worked. Thank You. Why was it set to only take the packages on the CD? IS it because I had installed it from a live CD?

Thanks,
John

---

### Post by aysiu on 2008-03-19
> **sparksandtabs said:**
> I am aware of the internet thing I was trying to point out the whole irony thing.....

And changing the software source worked. Thank You. Why was it set to only take the packages on the CD? IS it because I had installed it from a live CD?

Thanks,
John
Installing from the live CD has nothing to do with it. It probably commented out the online sources because it was unable to connect to the server during installation--either because your network connection had not yet been set up or because the server itself was down.

---

