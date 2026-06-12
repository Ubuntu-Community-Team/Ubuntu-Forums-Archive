---
title: "Vlc"
date: 2008-02-19
forum: General Help
---

### Post by anksi4u on 2008-02-19
when i go to add remove programs and just click on the vlc option i get this message in the description:-

VLC media player cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer typ


then when i try to install in the window that comes up..the status of almost all the packages seems to be coming failed....what do i do??

---

### Post by anksi4u on 2008-02-19
when i go to add remove programs and just click on the vlc option i get this message in the description:-

VLC media player cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer typ


then when i try to install in the window that comes up..the status of almost all the packages seems to be coming failed....what do i do??

---

### Post by vikramsharma on 2008-02-19
What are the specifications of your computer and also what version of Ubuntu are you running.  Please do inform in in detail so that we are able to help you out.

---

### Post by kpkeerthi on 2008-02-19
1. Enable universe and multiverse repositories from System -> Admin -> Software Sources
2. Run from command line
```

sudo aptitude update
sudo aptitude install vlc

```

---

### Post by Sukarn on 2008-02-19
Try installing vlc through Synaptic.
Go to System -> Administration -> Synaptic Package Manager and look for vlc.

---

### Post by anksi4u on 2008-02-19
i am using ubuntu 7.10 32 bit version and my lappy is amd athlon..

i tried  sudo aptitude update command and got the follwing result 

Fetched 7033B in 10s (666B/s)                                                   
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Couldn't rebuild package cache

---

### Post by erginemr on 2008-02-19
> **vikramsharma said:**
> What are the specifications of your computer and also what version of Ubuntu are you running.  Please do inform in in detail so that we are able to help you out.

I agree. This looks like a typical "installing 32 bit application on a 64 bit Ubuntu system" problem.

---

### Post by Yellow Pasque on 2008-02-19
That means you're using the 386 kernel and should switch to the generic kernel.
It also means you're not using an amd64 distro of Ubuntu and you're posting in the wrong forum.

---

### Post by Jouke74 on 2008-02-19
Or, he added the i386 repositories to his computer instead of the AMD64? :) Edit: never mind this, would be a different error.

---

### Post by p_quarles on 2008-02-19
The error description is actually kind of vague, and VLC is an open source project which is available for all common architectures. 

@anksi4u: Could you post the results of this terminal command?:
```
uname -a
```

---

### Post by khensucat on 2008-02-19
It means none of the above, necessarily. I get this error message all of the time in add/remove programs and have my box set up perfectly fine. Using synaptic works just fine to set up those same programs. I have no idea why add/remove programs gives those errors ;)

---

### Post by kpkeerthi on 2008-02-19
> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), **[COLOR="Red"]is another process using it?[/COLOR]**
E: Couldn't rebuild package cache


is another process using it? synaptic?

---

### Post by anksi4u on 2008-02-19
no process is using it...

---

### Post by PmDematagoda on 2008-02-19
If you are sure that no other process is using the package management system, just remove the lock file using:-
```
sudo rm /var/lib/dpkg/lock
```
and see if the problem is solved.

---

### Post by Kilz on 2008-02-19
> **p_quarles said:**
> The error description is actually kind of vague, and VLC is an open source project which is available for all common architectures. 

@anksi4u: Could you post the results of this terminal command?:
```
uname -a
```

From a duplicate post by the original poster in this thread.

> **anksi4u said:**
> result of uname -a

Linux ankit-laptop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

---

### Post by kpkeerthi on 2008-02-19
Another dup post here [http://ubuntuforums.org/showthread.php?t=701116](http://ubuntuforums.org/showthread.php?t=701116)

---

### Post by PmDematagoda on 2008-02-19
I have seen such errors being related to the software sources being commented out.

Open Software Sources in System>Administration>Software Sources and enable all the choices in the Ubuntu Software tab except for the CD-ROM, you may also make any changes in the other tabs according to your needs. After the changes are done, close the window, you will then be asked to reload the sources list, after that is complete you should be able to install VLC:).

---

### Post by PmDematagoda on 2008-02-19
The two duplicate threads have been merged.

Also the OP should is to understand that duplicate threads cannot be started on Ubuntu Forums and that one thread on a particular topic in the appropriate section should suffice.

This reminds me, this issue is not in a 64 bit Ubuntu OS, therefore it will be moved.

---

### Post by anksi4u on 2008-02-19
i am sorry for all these duplicate thread but the thing is that i am completely knew to linux and i tried installing ubuntu for weeks but couldnt do..i had to make many posts and all
and finally i got it running...
and now i deperately wish to install some player to play mp3 files and none of them seems to work

and also about the reload thing which you said even thats not happening.
in the download package section evrything is coming as failed...

---

### Post by PmDematagoda on 2008-02-19
How are you connected to the internet? Are you behind a proxy?

---

### Post by erginemr on 2008-02-19
Can you also please run this command:
```
gedit /etc/apt/sources.list
```
and copy what is inside this file and paste here?

---

### Post by anksi4u on 2008-02-20
no i am connected directly...and i am getting the updates done from the update manager..
so net connectivity is there...
and the out put of the command  **gedit /etc/apt/sources.list** is


# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

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
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted #Added by software-properties
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted #Added by software-properties
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-proposed universe main multiverse restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-proposed universe main multiverse restricted

---

