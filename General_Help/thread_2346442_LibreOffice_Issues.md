---
title: "LibreOffice Issues"
date: 2016-12-14
forum: General Help
---

### Post by daniel-w-miller on 2016-12-14
New to the forum.

I'm having issues with libreoffice since upgrading from Ubuntu 16.04 to 16.10.  I was getting package dependency errors when I tried updating software via software updater.  These errors were preventing any software from being updated.  Investigation showed they were package dependencies in LibreOffice that were causing this.  I then used synaptic to find those broken dependencies and removed them.  This in turn, removed LibreOffice.  Yikes.  I use this computer for work. However, now my other software does successfully update.  Now I am trying to install LibreOffice and it keeps failing with a segmentation fault....So, steps I have taken thus far:

1.  Removed broken packages in synaptic
2.  sudo apt-get -f install
3.  sudo dpkg --configure -a
4.  sudo apt-get install libreoffice  (I have also tried only installing each piece of libre such as writer and get the same errors)

I then get the following:

Unpacking libreoffice-common (1:5.2.2-0ubuntu2) ...
dpkg: error processing archive /tmp/apt-dpkg-install-dvTlJW/03-libreoffice-common_1%3a5.2.2-0ubuntu2_all.deb (--unpack):
 unable to open '/usr/lib/libreoffice/share/gallery/people/Presenter-Male2.png.dpkg-new': Operation not permitted
Segmentation fault (core dumped)

I seem to be stuck in an infinite loop of failure and I'm seeking the Oracle's guidance......

---

### Post by daniel-w-miller on 2016-12-14
OK.  So I posted this a little prematurely.  I did fix it, but I did want to post it here since I've seen a lot of issues with LibreOffice and Ubuntu 16.10.  To fix I did the following:

Opened synaptic
Did a search for libreoffice-common as this is what was producing all of the package dependency errors.  Synaptic also didn't report any dependency errors either.
Right click and went to "mark for suggested installation"
There were the packages whose dependencies were missing.
Marked all of them for installation
Hit apply

Works like a champ now and software updater is no longer giving me errors either.

---

### Post by vasa1 on 2016-12-14
If you come by here again, please mark the thread [SOLVED] as described here: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads). Thanks!

---

