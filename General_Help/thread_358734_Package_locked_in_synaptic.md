---
title: "Package locked in synaptic"
date: 2007-02-11
forum: General Help
---

### Post by mgmiller on 2007-02-11
I recently wanted to upgrade my flashplugin-nonfree from version 7 to 9 in Edgy.  I have backports enabled.  When I searched on flashplugin-nonfree, it shows I have 7 installed and the package is locked at the current version.  The problem is I can't unlock this package.  The Package>Lock Version has a check mark next to it and I can't get rid of it.  This is the only package that is locked, everything else works normally.  I have done a work around by doing the following:
 ```
sudo dpkg --remove --force-remove-reinstreq flashplugin-nonfree
sudo dpkg -P flashplugin-nonfree
```

This uninstalled the package and removed all the configuration files.  I then did a manual install from the flash web site.  Flash 9 works.  The problem is it is still listed as an uninstalled and locked package in synaptic.  

I would prefer to have synaptic track this package and update it as needed, rather than doing it manually all the time.

Any suggestions?

---

### Post by laidback on 2007-02-11
Is it possible to reinstall synaptic?

---

### Post by mgmiller on 2007-02-11
Although I could reinstall synaptic, I think the problem is deeper than that.  Synaptic is only a front end for apt.  I suspect it is just reporting some setting in apt somewhere and I don't know how to fix that.

---

### Post by CompShrink on 2007-02-19
I wanted to lock wine because versions above 0.9.20 don't work on dual screens, and I found synaptic's lock version won't enable a lock. After my research, it doesn't surprise me that it doesn't disable a lock either.

**The answer should be** to type the following in a terminal:

gksudo gedit /var/lib/synaptic/preferences

and delete anything that looks like:
Package: wine
Pin: version 0.9.9*
Pin-Priority: 1000

of course, different version number and flash instead of wine. Then you should be able to upgrade.

For more info on the problem if you're randomly curious like I naturally am:
[https://launchpad.net/ubuntu/+source/synaptic/+bug/67146](https://launchpad.net/ubuntu/+source/synaptic/+bug/67146)
[http://ubuntuforums.org/showthread.php?t=354388](http://ubuntuforums.org/showthread.php?t=354388)

---

### Post by mgmiller on 2007-02-20
At first, I just deleted the entry as you suggested, but since it was the only entry in the file, I got an error from synaptic causing it to close.  If I then changed the version number to something else, it allowed me to install the now unlocked package.

Thank you.

---

