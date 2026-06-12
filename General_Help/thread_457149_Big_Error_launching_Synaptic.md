---
title: "Big Error launching Synaptic"
date: 2007-05-28
forum: General Help
---

### Post by barkhat on 2007-05-28
I'm a farily new Linux/Ubuntu user and don't know that much.  Not sure where to post this but I"ll try here. 

I was trying to run the Synaptic (also tried the update manager as the orange icon is in the tray, as well as add-remove programs and automatix.  Nothing works) when something crashed. I got this:

E: Problem parsing dependency Depends
E: Error occurred while processing thekompany-support (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/www.getautomatix.com_apt_dists_feisty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

I have no idea where I"m supposed to report it, and even more importantly, how to fix it.  Please help!

Thank you.

---

### Post by Ek0nomik on 2007-05-28
I must say, one of my suggestions would be to get rid of Automatix.  ;)  Anything Automatix provides can be downloaded very easily yourself.

Anyways, here are some links to try and help you out:

[http://ubuntuforums.org/showthread.php?t=186672](http://ubuntuforums.org/showthread.php?t=186672)
[http://ubuntuforums.org/showthread.php?t=262582](http://ubuntuforums.org/showthread.php?t=262582)
[http://ubuntuforums.org/showthread.php?t=434988](http://ubuntuforums.org/showthread.php?t=434988)

---

### Post by arnieboy on 2007-05-28
> **barkhat said:**
> I'm a farily new Linux/Ubuntu user and don't know that much.  Not sure where to post this but I"ll try here. 

I was trying to run the Synaptic (also tried the update manager as the orange icon is in the tray, as well as add-remove programs and automatix.  Nothing works) when something crashed. I got this:

E: Problem parsing dependency Depends
E: Error occurred while processing thekompany-support (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/www.getautomatix.com_apt_dists_feisty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

I have no idea where I"m supposed to report it, and even more importantly, how to fix it.  Please help!

Thank you.
The erring package has long been fixed and a simple

```
sudo apt-get update
```

will fix this issue

---

### Post by barkhat on 2007-05-28
Thanks, guys.  Things seem to be back to normal from running the aptitude update.  I"m grateful  for your assists.

Whew!  That was close!

---

