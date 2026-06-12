---
title: "Installed Fluxbox PPA but no joy"
date: 2015-10-30
forum: General Help
---

### Post by vasa1 on 2015-10-30
I'm thinking of giving the Fluxbox window manager a try.

A visit to [http://fluxbox.org/download/](http://fluxbox.org/download/) tells me that the latest version is 1.3.7 but the version available from the standard Trusty repository is 1.3.5:

```
$ apt-cache policy fluxbox
fluxbox:
  Installed: (none)
  Candidate: 1.3.5-2
  Version table:
     1.3.5-2 0
      500 http://archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
$
```
A search of Launchpad pointed me to [https://launchpad.net/~adam-stokes/+archive/ubuntu/fluxbox](https://launchpad.net/~adam-stokes/+archive/ubuntu/fluxbox) which indicates that version 1.3.7 is available via a ppa for Trusty (which is what I'm on).

I ran```
sudo add-apt-repository ppa:adam-stokes/fluxbox
sudo apt-get update
sudo apt-get install fluxbox
```
But what I got was 1.3.5 and not 1.3.7. Checking *apt-cache policy fluxbox* gave me exactly the same output as before.

I ran```
sudo apt-get dist-upgrade
```and still wasn't offered Fluxbox 1.3.7.
I purged Fluxbox and tried again. Still 1.3.5.

I looked at Software Sources and the Fluxbox ppa is listed and ticked.

I looked at */etc/apt/* and there seem to be the same types of files there for the Fluxbox ppa as there are for other ppas I've successfully installed in the past.

**/etc/apt/sources.list.d/adam-stokes-fluxbox-trusty.list**```
deb http://ppa.launchpad.net/adam-stokes/fluxbox/ubuntu trusty main
# deb-src http://ppa.launchpad.net/adam-stokes/fluxbox/ubuntu trusty main
```

```
07:33 AM /etc/apt/trusted.gpg.d $ ll
total 28
drwxr-xr-x 2 root root 4096 Oct 30 23:46 ./
drwxr-xr-x 6 root root 4096 Nov 14  2014 ../
-rw-r--r-- 1 root root  364 Oct 30 23:46 adam-stokes-fluxbox.gpg
-rw-r--r-- 1 root root    0 Oct 30 23:46 adam-stokes-fluxbox.gpg~
-rw-r--r-- 1 root root  367 Sep  3 09:32 geany-dev-ppa.gpg
-rw-r--r-- 1 root root    0 Sep  3 09:32 geany-dev-ppa.gpg~
-rw-r--r-- 1 root root  362 Sep 10 11:44 linuxgndu-sqlitebrowser.gpg
-rw-r--r-- 1 root root    0 Sep 10 11:44 linuxgndu-sqlitebrowser.gpg~
-rw-r--r-- 1 root root  365 Jul  8 19:56 mc3man-trusty-media.gpg
-rw-r--r-- 1 root root    0 Jul  8 19:56 mc3man-trusty-media.gpg~
-rw-r--r-- 1 root root  346 Apr 21  2015 webupd8team-java.gpg
-rw-r--r-- 1 root root    0 Apr 21  2015 webupd8team-java.gpg~
07:33 AM /etc/apt/trusted.gpg.d $ 
```

**/etc/apt/sources.list**
```
07:36 AM /etc/apt $ grep -v "^#" sources.list

deb http://archive.ubuntu.com/ubuntu trusty main restricted
deb-src http://archive.ubuntu.com/ubuntu trusty main restricted

deb http://archive.ubuntu.com/ubuntu trusty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu trusty-updates main restricted

deb http://archive.ubuntu.com/ubuntu trusty universe
deb-src http://archive.ubuntu.com/ubuntu trusty universe
deb http://archive.ubuntu.com/ubuntu trusty-updates universe
deb-src http://archive.ubuntu.com/ubuntu trusty-updates universe

deb http://archive.ubuntu.com/ubuntu trusty multiverse
deb-src http://archive.ubuntu.com/ubuntu trusty multiverse
deb http://archive.ubuntu.com/ubuntu trusty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu trusty-updates multiverse


deb http://archive.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu trusty-security main restricted
deb http://archive.ubuntu.com/ubuntu trusty-security universe
deb-src http://archive.ubuntu.com/ubuntu trusty-security universe
deb http://archive.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu trusty-security multiverse

deb http://archive.canonical.com/ubuntu trusty partner

deb http://extras.ubuntu.com/ubuntu trusty main
07:37 AM /etc/apt $ 
```

Just, for clarity, I have never directly edited or modified any of the files in */etc/apt/*.


Any ideas on what I did wrong or on how to proceed?

---

### Post by deadflowr on 2015-10-30
Failed build of the ppa.
(in fact, the ppa maintainer only tried to build it twice, failing both times
I'm guessing those builds where for the different archs)

I see this quite often with firefox-trunk.

So, nothing you did was wrong.

---

### Post by vasa1 on 2015-10-31
> **deadflowr said:**
> Failed build of the ppa.
(in fact, the ppa maintainer only tried to build it twice, failing both times
I'm guessing those builds where for the different archs)

I see this quite often with firefox-trunk.

So, nothing you did was wrong.

Okay, thanks. I should have paid more attention to the screen contents!

Now that you pointed me in the right direction, I looked at [https://launchpad.net/~adam-stokes/+archive/ubuntu/fluxbox/+packages](https://launchpad.net/~adam-stokes/+archive/ubuntu/fluxbox/+packages) and see the "0 successful" and "2 failed" :(

---

