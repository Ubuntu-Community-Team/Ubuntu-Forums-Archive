---
title: "[SOLVED] Installed Packages"
date: 2008-01-16
forum: General Help
---

### Post by Javawag on 2008-01-16
<please delete this thread... wrong forum sorry!>

---

### Post by Javawag on 2008-01-16
Hi,

I've used synaptic to install a load of packages, but unfortunately I will have to reinstall linux Friday. Is there any way I can export a list of installed packages, and import it again later such that it downloads and installs all the installed packages again?

- Javawag

---

### Post by aysiu on 2008-01-16
All the packages are stored in /var/cache/apt/archives

If it's not the packages themselves but the list of packages you want, try this (it says it's for Edgy, but it should work for any Ubuntu release):
[HowTo: Create a list of installed packages](http://ubuntuforums.org/showthread.php?t=261366)

---

### Post by gilf on 2008-01-17
Thanks for the general procedure. But:

I know I've installed a lot more applications than I've found in /var/cache/apt/archives. Why is that?

I'd like to put my installed apps (via apt-move)  on a disk for installation on 4 other computers here. But where are they?

 I've mainly used Synaptic for installations. Is it possible Synaptic is just downloading the packages temporarily, installing, then discarding them?

I hope not -- I have a dialup, and it will be a lot of work to try to reconstruct and download all of those applications garnered over the last 2 months.

If so, how do I ensure that Synaptic preserves future downloads?

(Gutsy 7.10, Synaptic as default configured in initial system install)

---

### Post by Javawag on 2008-01-17
The list thing was what I wanted. Thanks a lot!!

- Javawag

---

### Post by gilf on 2008-01-18
> **Javawag said:**
> The list thing was what I wanted. Thanks a lot!!

- Javawag

Probably best to mark this thread "Solved," then.

I'll re-post my question in its own thread.

[http://ubuntuforums.org/showthread.php?t=671250](http://ubuntuforums.org/showthread.php?t=671250)

---

