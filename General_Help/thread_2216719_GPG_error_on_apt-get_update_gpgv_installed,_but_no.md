---
title: "GPG error on apt-get update: gpgv installed, but not executing."
date: 2014-04-13
forum: General Help
---

### Post by guerrero2 on 2014-04-13
Well, I got myself in a mess. 

running Ubuntu 13.10. Trying to watch Amazon Prime videos, but lacking some of the needed parts. 
Tried to install Synaptic to help find and install those needed parts. 

The following packages have unmet dependencies:
 synaptic : Depends: libept1.4.12 (>= 1.0.9) but it is not installable
            Recommends: rarian-compat but it is not installable
E: Unable to correct problems, you have held broken packages.

Found that exact problem elsewhere, with instructions on how to fix it. One step of the instructions is to run $ sudo apt-get update. It reads all the way through the packages, then delivers this:

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy Release: Could not execute 'gpgv' to verify signature (is gpgv installed?)

I have tried installing gpgv, and it assures me that it's installed and up to date. This is affecting the regular Ubuntu Software Center as well: it'll boot up, but it won't install anything and cites problems in the packages. I cannot find another thread with an error quite like this, so I turn to you. Help?

---

### Post by ibjsb4 on 2014-04-13
> E: Unable to correct problems, you have held broken packages.

Have you tried the fix broken packages command?

```
sudo apt-get -f install

```

---

