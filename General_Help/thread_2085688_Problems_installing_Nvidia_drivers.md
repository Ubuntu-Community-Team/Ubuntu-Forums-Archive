---
title: "Problems installing Nvidia drivers"
date: 2012-11-18
forum: General Help
---

### Post by efflandt on 2012-11-18
What is the expected or accepted way to install nvidia drivers now that **Additional Drivers** is not installed by default in 12.10?  Not sure what changed for the worse in 12.10 graphics, but default nouveau is very sluggish compared with previous versions and results in colored snow (even in just a terminal) if I try to scroll windows unless something else refreshes the screen.  My nvidia card is not really new or really old.

Since the powers at Ubuntu have been pushing their **Software Center** instead of the usual tools (Additional Drivers or Synaptic), I tried Software Center for installing nvidia current, but that totally messed up X after reboot. All I get after gui login is the background image with nothing else.  I am able to open a terminal with Ctrl+T, but that is all.  And if I go to a console with Ctrl+Alt+F1, once I login and try to stop lightdm all of the consoles disappear (cannot get to them anymore) and I am left on a black screen.  But if I move the cursor around, the login screen repaints like an Etch-A-Sketch and I am actually on the gui login screen.

I tried doing **nvidia-xconfig** from a root console in recovery mode (after remounting the drive read-write) and all that did was make the screen lower resolution with huge fonts in the login gui.  Still no X apps after login, just background image.

/var/log/apt/history.log shows:
Start-Date: 2012-11-17  20:50:54
Commandline: aptdaemon role='role-commit-packages' sender=':1.78'
Install: fakeroot:amd64 (1.18.4-2, automatic), screen-resolution-extra:amd64 (0.15, automatic), nvidia-current:amd64 (304.51.really.304.43-0ubuntu1), dkms:amd64 (2.2.0.3-1.1ubuntu1, automatic), python-xkit:amd64 (0.5.0, automatic), nvidia-settings:amd64 (304.51-0ubuntu2, automatic)
End-Date: 2012-11-17  20:51:30

But that did not work.  Apparently nouveau and nvidia do not cooperate like they do in 12.04, so X ends up unable to load any nvidia modules.

I am just glad I did not trash my perfectly working 12.04 system by upgrading it to 12.10, or I would have been really upset.

---

### Post by cariboo on 2012-11-18
Moved to a thread of it's own, as it was off topic in the thread it was in.

---

### Post by jerome1232 on 2012-11-18
Standard Method in 12.10 is to use the Additional Drivers tool. Click the cog wheel at top right, system settings, software sources, additional drivers.

It's just moved to a new spot is all.

---

### Post by efflandt on 2012-11-19
I found something in a web search that said to use apt-get to install **linux-sources**, **linux-headers-generic**, and **nvidia-current**.  So I booted using **rw single --verbose text** parameters (since I had trouble using console with things messed up).

But since nvidia-current was sort of installed by Software Center, it said I already had it and did not do anything, so I had to```
apt-get --reinstall install nvidia-current
```It is working fine now.

Once before I sent the nouveau group a BIOS dump of my GT 430, I wonder if they need it for the GTX 550 Ti, because the nouveau driver in 12.10 is dismally slow and snowy.

---

### Post by Parker32 on 2012-11-19
Due to the significant changes in Nvidia driver packages over the last year and the surrounding confusion in how these changes have effected installing and uninstalling Nvidia Drivers, a clear outline of what those changes are and how it effects users has become extremely important. 
This guide is intended to help both novice and experienced users understand how Nvidia drivers have changed their install and uninstall behavior when using Windows and what those changes mean.

---

### Post by bogan on 2012-11-19
> **Parker32 said:**
> Due to the significant changes in Nvidia driver packages over the last year and the surrounding confusion in how these changes have effected installing and uninstalling Nvidia Drivers, a clear outline of what those changes are and how it effects users has become extremely important. 
This guide is intended to help both novice and experienced users understand how Nvidia drivers have changed their install and uninstall behavior when using Windows and what those changes mean.What guide & where ??:

Please give a link.

---

