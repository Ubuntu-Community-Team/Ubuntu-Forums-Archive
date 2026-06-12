---
title: "Chromium snap directory permissions"
date: 2021-02-04
forum: General Help
---

### Post by Keith_Helms on 2021-02-04
How do I modify the Chromium snap so that it can access any directory?  

I install into small boot partitions (30 or 40gb) and my home directory mostly consists of links to other mount points.  I usually have 3 installs on my grub menu with the current LTS release, the previous one and another to play with.  Sharing files with a new install is just a matter of running a script to create some softlinks.

The new Chromium snap won't let me save to any of those mount points.  It won't even LIST them.  I went into the snap store and the Chromium permissions and enabled read system mount points (I think that was the title), but it didn't have any effect.

---

### Post by TheFu on 2021-02-05
> **Keith_Helms said:**
> How do I modify the Chromium snap so that it can access any directory?  

You cannot.  Snaps don't work that way.

You can only allow them to access your HOME (default) and places under /media/ and /mnt/ - those last 2 are possible only if the snap package maintainer decided that sort of access might be something needed. If they didn't, forget it.  Also, NFS isn't supported at all, last time I checked. Regardless, these other locations are not enabled by default.

[https://ubuntuforums.org/showthread.php?t=2434651&p=13923022#post13923022](https://ubuntuforums.org/showthread.php?t=2434651&p=13923022#post13923022)
$ snap connect chromium:removable-media
[https://snapcraft.io/docs/removable-media-interface](https://snapcraft.io/docs/removable-media-interface) has more and [https://snapcraft.io/docs/snap-confinement](https://snapcraft.io/docs/snap-confinement) explains more about snap limits.  Snaps are there to help grandma be protected from bad people and nearly always updated in addition to the program being able to run on any current version of Linux.  There are flaws for many of us.

There are a number of threads in these forums about snaps and allowed permissions.

---

### Post by Keith_Helms on 2021-02-05
Wow, when did Canonical become Microsoft (our way or the highway)?

I searched around and found Mint had developed their own deb package for Chromium and I installed that.   It lets me download to wherever I want.

It's the ulyssa deb file in [http://packages.linuxmint.com/pool/upstream/c/chromium/](http://packages.linuxmint.com/pool/upstream/c/chromium/)

---

### Post by ajgreeny on 2021-02-05
There are also PPA repositories for chromium, one of which I have been using for all the time since I moved to 20.04 and found the restrictions on using chromium snap in the manner I had become used to just too much to continue using it in the default version.  Even using ***sudo apt install chromium*** to install it suposedly from the from the standard repos simply installed the system to download and use the snapand not install it as a .deb package which I did not realise until until I first used it and was annoyed when I had the same problem as you have now seen.

The PPA I use is as shown at [https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev)

I have since then removed completely all snap packages from my system, Xubuntu 20.04, which seems to have a lower reliance on snap packages than Ubuntu, and I no longer have the ability to install them as snapd has also been removed.  To the best of my knowledge this has had no detrimental effect on my system in any way.

---

### Post by TheFu on 2021-02-05
> **Keith_Helms said:**
>  
I searched around and found Mint had developed their own deb package for Chromium and I installed that.   It lets me download to wherever I want. 

Directly installing .deb files often brings other undesirable repercussions. Got with a PPA instead and be certain to remove the .deb package first.

Email and web browsers can make good use of the constraints that snap packages provide for security. They just go a little to far, IMHO. There is little reason for gnome desktop or calculator applications to be snaps.  

Wish devs would ask, "should we" before they ask "can we."  Many snap packages clearly didn't ask that question.

---

### Post by Keith_Helms on 2021-02-05
> **TheFu said:**
> Directly installing .deb files often brings other undesirable repercussions.

I understand.  In this case, Mint 20 is built on top of Ubuntu 20.04, so my feeling was that using a deb package from it was less risky than getting one from some random source.

---

### Post by CelticWarrior on 2021-02-05
Better use the PPA suggested above. Much less risky and it updates automatically.

---

