---
title: "Ouch! My apt hurts..."
date: 2007-04-20
forum: General Help
---

### Post by PlancksCnst on 2007-04-20
I have some broken packages (I lost power in the middle of an installation), and am experiencing problems like[ this guy]("http://www.linuxquestions.org/questions/showthread.php?t=488534") had.  Only, upgrading worked for him; it doesn't for me.  I still get the error that "subprocess pre-removal script returned error exit status 2" and "subprocess post-installation script returned error exit status 2" when following the instructions in the last response.  He mentions fixing said scripts, but I don't know where they are.  How do I find them?

Or, is there another way around this problem?

---

### Post by DougieFresh4U on 2007-04-20
Not sure about this but can you access a terminal and do **sudo apt-get -f install** and then **sudo dpkg --configure -a** Hope that helps:)

---

### Post by Ziggy72 on 2007-04-21
I would suggest:

Synaptic Package Manager > Custom Filters > Broken

to find and delete any broken packages.

---

### Post by PlancksCnst on 2007-04-21
Thanks.  I've tried the force option before, and it doesn't work.  I've also tried forcing remove; same thing.  In Synaptic package  manager, nothing shows up as broken.  I've tried removing the problem packages through Synaptic, and it doesn't work.

---

### Post by PlancksCnst on 2007-04-21
Just in case this helps...
output from sudo apt-get -f install...
```


Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 81 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up xscreensaver (4.24-4ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing xscreensaver (--configure):
 subprocess post-installation script returned error exit status 2
Setting up xubuntu-artwork-usplash (0.11) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing xubuntu-artwork-usplash (--configure):
 subprocess post-installation script returned error exit status 2
Setting up xubuntu-default-settings (0.23) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing xubuntu-default-settings (--configure):
 subprocess post-installation script returned error exit status 2
Setting up xubuntu-docs (6.05.5) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing xubuntu-docs (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 xscreensaver
 xubuntu-artwork-usplash
 xubuntu-default-settings
 xubuntu-docs
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by DougieFresh4U on 2007-04-21
Did you try the 2 codes I posted earlier?

---

### Post by PlancksCnst on 2007-04-21
> **DougieFresh4U said:**
> Did you try the 2 codes I posted earlier?

Yes, and I posted the output above (comment #5)

---

### Post by PlancksCnst on 2007-04-22
I ended up fixing it; here's how:

I searched for prerm on my system, and found the scripts to be in /var/lib/dpkg/info
I attempted to edit the problem scripts; they were completely corrupted.  I deleted them (I had read that when you build a package, they are optional, so theoretically, dpkg would continue on if they weren't there)
I was then able to uninstall (and subsequently reinstall) the problem packages.

---

### Post by mattymattysidebyeach on 2007-11-29
:guitar:
thanks very much for this handy solution.

This certainly will be useful in the future for system tweaking.

---

