---
title: "Added repositories do not seem to be getting used for Java or VirtualBox"
date: 2016-08-03
forum: General Help
---

### Post by Myiasia on 2016-08-03
So I spent all night trying to get my computer up and running, only to find out I couldn't upgrade from 15.04 to 16.04.1. So I did a fresh install, and went and edited my sources.list to include the repositories for stuff I need/want to run. This is what it looks like:

# All the stuff that comes with/for Xenial
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted universe multiverse

# Oracle VirtualBox
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) xenial non-free contrib

# wine
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) xenial main
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) xenial main

# Java
deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) xenial main

# Old XMMS (and required stuff)
deb [http://www.pvv.ntnu.no/~knuta/xmms/karmic](http://www.pvv.ntnu.no/~knuta/xmms/karmic) ./
deb-src [http://www.pvv.ntnu.no/~knuta/xmms/karmic](http://www.pvv.ntnu.no/~knuta/xmms/karmic) ./
# Apparently the last version of libmikmod2 is in Karmic's repositories, so:
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) karmic main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) karmic main restricted universe multiverse

Now, Java won't even show up in the software I can get (even though "Hit:8 [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) xenial InRelease") and VirtualBox installed, but from Ubuntu's repositories despite "Hit:1 [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) xenial InRelease"... wine, on the other hand, grabbed from its repos just fine and dandy.

... so what the heck am I doing wrong? This is how I did it on every build before 16.04 and it worked just fine. I see rapid hair loss in my future if I can't figure this out soon. And I was just considering making the switch permanently from Windows... until this happened.

Footnote: Yes, I used the add-apt-repository command for VirtualBox and Java (and tried to install them afterwards) first, then I moved their /sources.list.d/respective-software.list contents to the /etc/apt/sources.list and tried again, with the same results. I'm not an expert with Ubuntu (or any flavor of Linux, for that matter), but I DO know how to follow instructions and have been using Linux off and on (a lot) for probably 14 years now.

---

### Post by howefield on 2016-08-03
Shouldn't the Virtualbox line read..

```
deb http://download.virtualbox.org/virtualbox/debian xenial contrib
```

and the java line be..

```
deb http://ppa.launchpad.net/webupd8team/java/ubuntu xenial main
```

---

### Post by Myiasia on 2016-08-03
Well, look at that! At least, the java line. I'm not sure why it put the "deb-src" and not just the "deb" part - I got that straight from the files that were created when I used the add-apt-repository command. I'll see what it does with the suggested changes, though the virtualbox entry should still work the way it is.

---

### Post by Myiasia on 2016-08-03
Well, that fixed Java. VirtualBox isn't showing any new updates, though, so I suspect the one available through normal channels is already up-to-date.

Yay!
java version "1.8.0_101"
Java(TM) SE Runtime Environment (build 1.8.0_101-b13)
Java HotSpot(TM) 64-Bit Server VM (build 25.101-b13, mixed mode)

And thanks a bunch!

---

