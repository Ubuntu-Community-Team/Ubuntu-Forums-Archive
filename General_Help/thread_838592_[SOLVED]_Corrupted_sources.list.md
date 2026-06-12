---
title: "[SOLVED] Corrupted sources.list"
date: 2008-06-23
forum: General Help
---

### Post by tawmas on 2008-06-23
Hello, all!

It looks like my /etc/apt/sources.list got somewhat corrupted during the last testing cycle, so I wonder if there's a quick way to rebuild it or grab a fresh version. Failing that, I hope that someone can be so kind as to post a sample.

I'm on Hardy, 64 bit.

---

### Post by Rocket2DMn on 2008-06-23
Can you post it for us?
```
cat /etc/apt/sources.list
```
Also, can you post the error?  Usually it is as easy as a one line fix.

Also, googling found a page with a link to this: [http://www.compsoc.nuigalway.ie/~slibuntu/test/files/sources.list](http://www.compsoc.nuigalway.ie/~slibuntu/test/files/sources.list)
I would try and fix yours first, though.

Don't forget to update after you change the sources.list file
```
sudo apt-get update
```

---

### Post by tawmas on 2008-06-23
I've got at least three different kinds of errors:

1) attempting to install syslinux and mtools (as per [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) and [http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/](http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/)) fails:

```
tawmas@tylke:~$ sudo apt-get install mtools 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mtools is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mtools has no installation candidate

```

2) I get 404 errors on some of the sources:

```
W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/hardy/main/binary-amd64/Packages.gz  404 Not Found

W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/hardy/restricted/binary-amd64/Packages.gz  404 Not Found

W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/hardy/universe/binary-amd64/Packages.gz  404 Not Found

W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/hardy/multiverse/binary-amd64/Packages.gz  404 Not Found

```

3) I seem to pick up software updates correctly, but just after applying them, synaptic tells me something like "39 days since last check". Also, every day for about half of the day I have the "download error" icon in the notification area (my Internet link is up and full speed when this happens, so it's not a general networking problem)

Finally, here's my full sources.list as requested:

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Beta amd64 (20080319)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ports.ubuntu.com/ubuntu-ports hardy main restricted
deb-src http://ports.ubuntu.com/ubuntu-ports hardy main

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ports.ubuntu.com/ubuntu-ports hardy universe
deb-src http://ports.ubuntu.com/ubuntu-ports hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ports.ubuntu.com/ubuntu-ports hardy multiverse
deb-src http://ports.ubuntu.com/ubuntu-ports hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://ppa.launchpad.net/banshee-team/ubuntu hardy main

```

---

### Post by Rocket2DMn on 2008-06-23
Sounds like your repositories may be screwed up.  Try going to System->Administration->Software Sources and choosing a new repository which should fix your second problem. From here you can enable the universe and multiverse repositories which should fix your first problem.

You can then run from terminal:
```
sudo apt-get update
sudo apt-get upgrade
```
There will probably be a lot of updates for you.

---

### Post by tawmas on 2008-06-23
First of all, thanks for your prompt replies.

Sadly, it looks like things are more screwed than we thought...

After posting my sources.list I noticed I have no archive.ubuntu.com source for main, universe and multiverse, just ports.ubuntu.com (which all fail). So I hand edited my sources.list to substitute all of those entries with references to archive.ubuntu.com and ran an apt-get update.

No errors. And magically mtools and syslinux become installable (I just tested with -s, but didn't install, as I fear this would pick the 32 bit version and I don't know how to verify that prior to installation).

Then, I read your reply, and tried to select "Main server" in Software Sources. Errors are back, as are those ports.ubuntu.com references in my sources.list. :-(

I tried to pick another server in Software Sources, but the list of mirros is empty... :-(

I just don't know what to do next. I'll probably just hand edit my sources.list file again and hope I won't be picking 32 bit packages instead of 64 bit ones...

---

### Post by Bubba64 on 2008-06-23
I have never used a 64 bit set up, but editing your apt source list without knowing exactly what your doing, and having no fear of borking your system and losing important stuff would be okay. Somebody will show you their list and I suspect that you can find a source listing on Google.:) Don't let your need for immediate results boink your setup or make the problem way more complex.

---

### Post by tawmas on 2008-06-23
Looks like my home-made solution is working... I was able to update and get a sane message afterwards ("Last updated less than one hour ago"), also I was able to install syslinux and mtools and it picked up the 64 bit debs!

The list of servers in Software Sources is still empty, though, and I will probably never understand what broke my APT configuration in the first place... Oh, well, I can live with that! ;-)

Thanks again for you support, it was appreciated!

---

### Post by tawmas on 2008-06-23
> **Bubba64 said:**
> I have never used a 64 bit set up, but editing your apt source list without knowing exactly what your doing, and having no fear of borking your system and losing important stuff would be okay. Somebody will show you their list and I suspect that you can find a source listing on Google.:) Don't let your need for immediate results boink your setup or make the problem way more complex.

Oh, well, I went through all the alphas and betas since I started using Ubuntu (late in the Feisty release cycle), and I'm almost ready to jump to Intrepid, so I don't fear some breakage and wild experimentation! :-)

Right now, I'm trying to put a bootable live on an USB key so that I can bork my brand new eee 900 too! ;-)

---

### Post by Rocket2DMn on 2008-06-23
It automatically detects your installation type, so it will get 64 bit packages when available.  Glad it's working now.

---

### Post by Bubba64 on 2008-06-23
> **tawmas said:**
> Oh, well, I went through all the alphas and betas since I started using Ubuntu (late in the Feisty release cycle), and I'm almost ready to jump to Intrepid, so I don't fear some breakage and wild experimentation! :-)

Right now, I'm trying to put a bootable live on an USB key so that I can bork my brand new eee 900 too! ;-)

Happy borking it sounds like you know enough to mess around. A lot of people come on the threads and just flail at their machines and end up like I did in the 1st 6 months of 3 re images, I didn.t discover this forum until I actually new what not to due to have a stable setup. :)

---

