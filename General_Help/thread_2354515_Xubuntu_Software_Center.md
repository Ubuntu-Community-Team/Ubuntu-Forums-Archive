---
title: "Xubuntu Software Center"
date: 2017-03-03
forum: General Help
---

### Post by dunya on 2017-03-03
I have uninstalled Xubuntu's original software center and installed Ubuntu Software Center. Will the packages from Ubuntu SC will work without problem in Xubuntu? Also, digged internet but couldn't find how to reinstall Xubuntu's original Software Center, is there any way to install it?

---

### Post by oldos2er on 2017-03-03
> **dunya said:**
> I have uninstalled Xubuntu's original software center and installed Ubuntu Software Center. 

I'm unaware of any difference between those two apps. Isn't there just one software-center program?

> **dunya said:**
> Will the packages from Ubuntu SC will work without problem in Xubuntu? 

The repositories, along with their packages, are exactly the same.

---

### Post by howefield on 2017-03-03
There are two packages..

```
apt-cache policy *-software
gnome-software:
  Installed: 3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1
  Candidate: 3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1
  Version table:
 *** 3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1 500
        500 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     3.20.1+git20160420.1.ca63436.ubuntu-xenial-0ubuntu2 500
        500 http://gb.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
ubuntu-software:
  Installed: 3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1
  Candidate: 3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1
  Version table:
 *** 3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1 500
        500 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     3.20.1+git20160420.1.ca63436.ubuntu-xenial-0ubuntu2 500
        500 http://gb.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
```

I think ubuntu-software is the old (original) Software Centre and the gnome-software is the new package.

---

### Post by oldos2er on 2017-03-03
Today I learned! Thanks howefield.

---

### Post by dunya on 2017-03-03
> **howefield said:**
> There are two packages..

```
apt-cache policy *-software
gnome-software:
  Installed: 3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1
  Candidate: 3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1
  Version table:
 *** 3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1 500
        500 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     3.20.1+git20160420.1.ca63436.ubuntu-xenial-0ubuntu2 500
        500 http://gb.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
ubuntu-software:
  Installed: 3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1
  Candidate: 3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1
  Version table:
 *** 3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1 500
        500 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     3.20.1+git20160420.1.ca63436.ubuntu-xenial-0ubuntu2 500
        500 http://gb.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
```

I think ubuntu-software is the old (original) Software Centre and the gnome-software is the new package.

So please ELI5, should I install gnome-software as it is new?

---

### Post by howefield on 2017-03-03
> **dunya said:**
> ELI5

Well, to be honest both ubuntu-software and gnome-software are among the first applications I uninstall when setting up Ubuntu, due to a preference in using the terminal, I like the feedback that you get from the command line which is often absent (at least, not easily visible) from graphical package manager applications.

As I understand it ubuntu-software is the "old" Ubuntu Software Centre and was replaced in 16.04 with gnome-software and called Ubuntu Software. Both will work and either or should be good for you but the newer one is gnome-software. It has been very much improved since the release of 16.04 back in April last year.

I don't run Xubuntu that often so I'm sure if I have gotten anything incorrect someone will come along and put us right :)

So bottom line, install gnome-software if you want the newest Software Manager.

---

### Post by yoshii on 2017-03-03
I find that it's convenient to have more than one of those types of programs installed.   I typically install both the old-fashioned Ubuntu Software Center as well as Synaptic Package Manager (very reliable!) and Gnome Software.   I even sometimes dabble with Lubuntu Software Center which has some things which don't always conflict with non-Lubuntu stuff too (although it can be risky).  Gnome-Disks, for example is nice to have.   Also, I install gDebi Package Manager (gdebi) and that's VERY handy.  I hope this is helpful to you.

---

### Post by bearlake on 2017-03-03
> **yoshii said:**
> I find that it's convenient to have more than one of those types of programs installed.   I typically install both the old-fashioned Ubuntu Software Center as well as Synaptic Package Manager (very reliable!) and Gnome Software.   I even sometimes dabble with Lubuntu Software Center which has some things which don't always conflict with non-Lubuntu stuff too (although it can be risky).  Gnome-Disks, for example is nice to have.   Also, I install gDebi Package Manager (gdebi) and that's VERY handy.  I hope this is helpful to you.

Ohhh my... Not a little much?

Command line install or Synaptic Package Manager does it for me.

---

### Post by deadflowr on 2017-03-03
> **dunya said:**
> So please ELI5, should I install gnome-software as it is new?

ubuntu-software or gnome-software are the basically the same.
the old software center was software-center.

Ubuntu replaced software-center with gnome-software and ubuntu-software is like an added layer to that, fully dependent on the gnome-software package.
(I'm not sure what, exactly ubuntu-software package actually brings, i would guess the snap package installation options, or maybe the software reviews?) 
So, basically, even if you try to just install ubuntu-software, you will be getting gnome-software as well.

But luckily, this is not in reverse, as gnome-software, can stand on it's own.

If that makes sense.

---

