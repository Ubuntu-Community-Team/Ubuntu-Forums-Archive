---
title: "Restore a package to original version"
date: 2013-12-10
forum: General Help
---

### Post by jamesharper-caesar on 2013-12-10
Hi, I've been been having some problems with my touchpad since a dist-upgrade I did a few days ago. The touchpad works but runs off the mouse settings and had lost many of its features such as vertical scroll and emulated middle click.

I think the problem is the new version of xserver-xorg-input-synaptics installed with the dist-upgrade so I was wondering how to restore xserver-xorg-input-synaptics to the version when I first installed Ubuntu on my laptop. I'm running 12.04.

Thank you in advance for any help!

---

### Post by ian-weisser on 2013-12-12
You can downgrade a package using the *dpkg* command, but it's not a supported nor tested action.

This is the actual warning on the subject from the *dpkg* man page:
>               Warning:  At present dpkg does not do any dependency checking on
              downgrades and therefore will not  warn  you  if  the  downgrade
              breaks the dependency of some other package. This can have seri&#8208;
              ous side effects, downgrading essential  system  components  can
              even make your whole system unusable. Use with care.

How you do it:
1) Backup your data
2) Create an install media in case this destroys your system.
3) Download the original deb package (version 1.5.99.902-0ubuntu5) from [http://packages.ubuntu.com](http://packages.ubuntu.com).
4) Put the package in your /var/cache/apt/archive/
5) Use the command **sudo dpkg --force-downgrade xserver-xorg-input-synaptics**
I have never used force-downgrade, so the syntax may be slightly off.

If downgrading does break your system or cause data loss, there is not much we can do beyond advising a reinstall.

---

