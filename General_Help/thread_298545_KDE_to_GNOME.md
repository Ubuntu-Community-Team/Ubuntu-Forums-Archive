---
title: "KDE to GNOME"
date: 2006-11-12
forum: General Help
---

### Post by thekingof7 on 2006-11-12
I jsut installed 6.10 edgy KDE from a cd, I am really hating it, is there anyway of going over to GNOME without losing all my files? I dont care if I lose all of my programs btw.

---

### Post by igknighted on 2006-11-12
Just install the package ubuntu-desktop via aptitude or synaptic or however you like.  You will then have the option of loging into KDE or GNOME.  Nothing will be lost.  I'm just wondering why you'd want to do that :-P

---

### Post by aysiu on 2006-11-12
Follow these directions to install Gnome:
[http://www.psychocats.net/ubuntu/gnome](http://www.psychocats.net/ubuntu/gnome)

Then follow these directions to remove KDE:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by thekingof7 on 2006-11-12
Well, I just really liked GNOME it seems to wrok better w/ my machine, dont get ym wrong KDE is pretty, but GNOME jsut ran smoother.

---

### Post by thekingof7 on 2006-11-12
btw @aysiu your link on how to install GNOME jsut takes me to a blank page.

---

### Post by aysiu on 2006-11-12
> **thekingof7 said:**
> btw @aysiu your link on how to install GNOME jsut takes me to a blank page.
Doesn't for me. Could it be something wrong with your browser?

Have you tried refreshing the page?

---

### Post by igknighted on 2006-11-12
> **thekingof7 said:**
> Well, I just really liked GNOME it seems to wrok better w/ my machine, dont get ym wrong KDE is pretty, but GNOME jsut ran smoother.

I'm just kidding around... I love KDE, but you can't beat the choices in linux... if you don't like one desktop, pick one of the others

---

### Post by thekingof7 on 2006-11-13
Well I can view the page now, but now wehn I type the "sudo aptitude install ubuntu-desktop" command it says there is no package avalibel under that name, or somthing to that effect. Help.

---

### Post by aysiu on 2006-11-13
> **thekingof7 said:**
> Well I can view the page now, but now wehn I type the "sudo aptitude install ubuntu-desktop" command it says there is no package avalibel under that name, or somthing to that effect. Help.
Can you post the output of this command? ```
cat /etc/apt/sources.list
```

---

### Post by thekingof7 on 2006-11-13
## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

#deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) edgy free non-free
#deb-src [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) edgy free non-free



btw I notcied somthing in that tut it says "ubuntu-desktop" and I get nothing, but whne i put "ubuntu desktop" I get stuff, it jsut say somthing to the effect of there are similar packages avalible.

---

### Post by rfruth on 2006-11-13
Hey Aysiu psychocats.net comes up fine for me but some are not familiar with aptitude (thanks for all you have done & continue to do) :)

---

### Post by thekingof7 on 2006-11-13
okay thats great but i still need some help.

---

### Post by thekingof7 on 2006-11-13
Is anyone planning on helping out here?

---

### Post by aysiu on 2006-11-13
Have patience? Two hours is nothing in forum time.

Your /etc/apt/sources.list looks fine. Can you post the output of these commands? ```
sudo aptitude update
aptitude search ubuntu-desktop
sudo aptitude install ubuntu-desktop
```

---

### Post by thekingof7 on 2006-11-13
Sorry for being impatient, Im jsut really trying to get this thing going. 



Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Get:4 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages [1220kB]
99% [6 Packages gzip 0]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
  Sub-process gzip returned an error code (1)
Fetched 6B in 1s (4B/s)
Reading package lists... Done
john@john-desktop:~$ aptitude search ubuntu-desktop
john@john-desktop:~$ sudo aptitude install ubuntu-desktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "ubuntu-desktop"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

---

### Post by aysiu on 2006-11-13
This looks to be the problem: ```
Get:6 http://archive.ubuntu.com edgy/main Packages [1220kB]
99% [6 Packages gzip 0]
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com edgy/main Packages
Sub-process gzip returned an error code (1)
``` especially since *ubuntu-desktop* is in the main repositories. Can you try using a mirror instead? What country do you live in?

---

### Post by thekingof7 on 2006-11-13
I thought I might need to change to a different date base, I read about some guy with the same problem changing to a mirror in Germany. Oh btw Im in Wisconsin (USA). Thank you.

---

### Post by aysiu on 2006-11-13
Okay, Wisconsin.

Then what I'd do is edit your /etc/apt/sources.list: ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
kdesu kate /etc/apt/sources.list
``` Make sure all your repositories are the US mirrors. So instead of *deb [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy main* you'd substitute in *deb [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy main*. Then save and exit. Finally, do ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
``` See if you still get taht same *sub-process gzip returned an error code (1)* error.

---

### Post by Velotix on 2006-11-13
I have a similar issue related to this: I can try to download *ubuntu-desktop* but it tells me that it clashes with existing software packages and it tries to resolve the dependencies by not installing the ubuntu-desktop package at all and some additional dependency packages [(my zero-reply thread on the subject here :( )](http://www.ubuntuforums.org/showthread.php?t=297919). Zero replies suggests zero answers, but then I saw this thread.

This and your experience leads me to suggest that the Edgy version of *ubuntu-desktop* may be broken. Don't know how to confirm this.

**EDIT:** Just saw aysiu's post. I'm using the UK mirror myself, so perhaps that's the problem. I'll check now.

**EDIT THE SECOND:** Hmm. I got an odd response from the Terminal, but usually the program runs anyway.

```
$ kdesu kate /etc/apt/sources.list
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```

I know a workaround for this but it shouldn't return this error in the first place.

**EDIT THE THIRD:** Well, the original repositories work for me, but I have the same problem. Looks like I have no choice but to break my Xubuntu installation to resolve the conflict. Great.

---

### Post by thekingof7 on 2006-11-14
Well I ended up jsut installing from the cd. Oh well. And Im still getting that error with the repositories.

---

### Post by igknighted on 2006-11-14
> **Velotix said:**
> I have a similar issue related to this: I can try to download *ubuntu-desktop* but it tells me that it clashes with existing software packages and it tries to resolve the dependencies by not installing the ubuntu-desktop package at all and some additional dependency packages [(my zero-reply thread on the subject here :( )](http://www.ubuntuforums.org/showthread.php?t=297919). Zero replies suggests zero answers, but then I saw this thread.

This and your experience leads me to suggest that the Edgy version of *ubuntu-desktop* may be broken. Don't know how to confirm this.

**EDIT:** Just saw aysiu's post. I'm using the UK mirror myself, so perhaps that's the problem. I'll check now.

**EDIT THE SECOND:** Hmm. I got an odd response from the Terminal, but usually the program runs anyway.

```
$ kdesu kate /etc/apt/sources.list
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```

I know a workaround for this but it shouldn't return this error in the first place.

**EDIT THE THIRD:** Well, the original repositories work for me, but I have the same problem. Looks like I have no choice but to break my Xubuntu installation to resolve the conflict. Great.

The error you get when launching Kate is perfectly normal... I get it in every distro I've ever used, not jsut Ubuntu.  I never have figured out what causes it, but I've always been told its normal and it wont adversely affect anything.

---

### Post by thekingof7 on 2006-11-14
I fixed the repositoty problem. Go to the ubuntuguide wiki, and go to the repositories section, copy them over you current repositories, waaaay more reliable.

---

