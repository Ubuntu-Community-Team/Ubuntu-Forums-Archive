---
title: "Mess with python! Can I reinstall it?"
date: 2006-11-20
forum: General Help
---

### Post by Homayoon on 2006-11-20
Only a few days after "converting" to Ubuntu (Dapper), I made a *REAL* mess with Python and now many Python applications don't run --BitTorrent and Alacarte for example. As an example, Alacarte when run from a terminal raises this error message "...<call staclk>...ImportError: /usr/lib/python2.4/lib-dynload/math.so: undefined symbol: PyFPE_jbuf"

The mess I made involved building and installing Python 2.4, Python 2.5, Stackless (on both), wxPython 2.6 and wxPython 2.7 (some of them more than once!). I thought I may be able to reinstall Python using Synaptic (Windows like solution? If it is, I am so sorry! I've just come to Ubuntu after all) but the "Mark for reinstallation" option is not available, and removing it also seems like a nightmare because of zillions of other programs depending on it. Can I get around the mess anyhow? Or I should live the rest of my days without the missing programs!! :mrgreen:

---

### Post by Choad on 2006-11-20
open up a terminal and type 

sudo apt-get install --reinstall <python>

where <python> is the name of the python package you want to reinstall

---

### Post by Homayoon on 2006-11-20
Unfortunately it didn't help. I ran: 

sudo  apt-get install --reinstall python

and this is the result:

```

Reading package lists... Done
Building dependency tree... Done
Reinstallation of python is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

running "sudo  apt-get install --reinstall python2.4" also displays similar results.

---

### Post by lazyart on 2006-11-20
what does your sources.list look like?

---

### Post by Homayoon on 2006-11-20
Here it is:

```

## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.
## You may replace "us" with your country code to get the closest mirror.

deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## MAJOR BUG FIX UPDATES produced after the final release
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

## UNIVERSE AND MULTIVERSE REPOSITORY (Unsupported by Ubuntu.  Use at own risk.)deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/ubuntu/plf breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf breezy free non-free

deb http://www.beerorkid.com/compiz dapper main
deb http://ubuntu.compiz.net/ dapper main

```

---

