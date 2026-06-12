---
title: "[SOLVED] Error with Wine in Gutsy"
date: 2007-10-29
forum: General Help
---

### Post by HelixAgent on 2007-10-29
Greetings all!,

I have the following problem, I have a clean install of Ubuntu Gutsy and obviously there is no Wine installed, so I proceeded to install it by adding the repository the Wine HQ.com website gives me for Gutsy, I add the repository via Terminal and when I click "check" on the Update Manager to get Wine this line appears as an error: 

"W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263"

How can I fix that? What does the Public Key means and how can it be fixed?
Thank you!

---

### Post by taurus on 2007-10-29
Run this line from a terminal.

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

---

### Post by Maestro23 on 2007-10-29
> > **HelixAgent said:**
> Greetings all!,

I have the following problem, I have a clean install of Ubuntu Gutsy and obviously there is no Wine installed, so I proceeded to install it by adding the repository the Wine HQ.com website gives me for Gutsy, I add the repository via Terminal and when I click "check" on the Update Manager to get Wine this line appears as an error: 

"W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263"


How can I fix that? What does the Public Key means and how can it be fixed?
Thank you!

Did you add the key 1st?: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

[QUOTE]Adding the WineHQ APT Repository:

First, open a terminal window. Then add the repository's key to your system's list of trusted APT keys by copy and pasting the following:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

Next, add the repository to your system's list of APT sources:


---

### Post by HelixAgent on 2007-10-30
Thank you! I added the Key and then added the Repository but now nothing happens! The Wine Installation option does not appears in the Update manager and when I try "sudo apt-get update" and then "sudo apt-get install wine" nothing happens! it says this:

"user@ubuntu:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: libaudio2 but it is not installable
E: Broken package"

What can I do? I know its not a Bug because for what it seems other people have already installed wine in Gutsy!

---

### Post by Maestro23 on 2007-10-30
In Synaptic under Edit, Try the** Fix Broken packages** option.  Run your update and install attempt again.

---

### Post by HelixAgent on 2007-10-30
Nothing! Didn't work, it said "Succesfully fiex dependency problems" when I clicked "Edit > Fix broken packages" and then run both codes in terminal "sudo apt-get update" and "sudo apt-get install wine" AND after getting the same error I tried in the update manager and no changes.

---

### Post by Maestro23 on 2007-10-30
> **HelixAgent said:**
> Nothing! Didn't work, it said "Succesfully fiex dependency problems" when I clicked "Edit > Fix broken packages" and then run both codes in terminal "sudo apt-get update" and "sudo apt-get install wine" AND after getting the same error I tried in the update manager and no changes.

Wine is looking for libaudio2.  Can you:

> sudo apt-get install libaudio2

Should be there, I just searched for it.

---

### Post by HelixAgent on 2007-10-30
Hahaha look what it says!

trino@ubuntu:~$ sudo apt-get install libaudio2 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libaudio2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libaudio2 has no installation candidate

Hahahaha obsoleted? Why is that!
Hey! Thanks a lot for helping me! sorry to bother you!

---

### Post by Maestro23 on 2007-10-30
> **HelixAgent said:**
> Hahaha look what it says!

trino@ubuntu:~$ sudo apt-get install libaudio2 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libaudio2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libaudio2 has no installation candidate

Hahahaha obsoleted? Why is that!
Hey! Thanks a lot for helping me! sorry to bother you!

What do your Software Sources look like?  Mine is below:

---

### Post by HelixAgent on 2007-10-30
Like this:

---

### Post by Maestro23 on 2007-10-30
> **HelixAgent said:**
> Like this:

What about Third-Party?

---

### Post by HelixAgent on 2007-10-30
Here it is:

---

### Post by Maestro23 on 2007-10-30
Can you post your** /etc/apt/sources.list**

> cat /etc/apt/sources.list

Copy & Paste here.

---

### Post by HelixAgent on 2007-10-30
Here:

# 
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

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
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties

---

### Post by Maestro23 on 2007-10-30
No wonder you can't find anything and are having issues, all your sources are commented out (#).  Did you upgrade from Feisty?

Here's my list:

> # deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security multiverse


Uncomment your sources then do:

sudo apt-get update

---

### Post by HelixAgent on 2007-10-30
Hahaha and why did that happen? I did not upgraded I made a clean install! Let me try that out!

---

### Post by Maestro23 on 2007-10-30
> **HelixAgent said:**
> Hahaha and why did that happen? I did not upgraded I made a clean install! Let me try that out!

Well, no one was looking over your shoulder, so it's no telling what you did for that to happen. :)

Future Reference:  The following link can generate a sources.list for you, should you ever need a fresh one down the road.

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by HelixAgent on 2007-10-30
LOL! Thank you so much! Everything is working now! Downloading Wine right now! Thank you!!!

---

### Post by Maestro23 on 2007-10-30
> **HelixAgent said:**
> LOL! Thank you so much! Everything is working now! Downloading Wine right now! Thank you!!!

Good deal man.  Glad we could get it resloved. Mark down all you learned in this thread.  You may need it down the road for yourself or to help someone else.:)

Don't forget to mark this SOLVED using the Thread Tools.:guitar:

---

### Post by HelixAgent on 2007-10-30
I will! Thank you so much again! Cheers!

---

### Post by boegeskov on 2007-12-29
worked perfectly.  thanks for the help.

---

### Post by y-aji on 2008-03-05
Also had great results for me! I think ubuntu may be disabling alot of sources.list by default, now.. This is the third pc in a row I've had to fight with the sources.list file.  Thanks all!

:KS

---

