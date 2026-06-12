---
title: "Syaptic troubles..."
date: 2013-03-15
forum: General Help
---

### Post by DrDanco on 2013-03-15
I should mention that I still suck at using Linux, but I'm trying to learn xD
There were a few sections that this might fit it, but this seemed the most appropriate, sorry if I'm wrong :P

So this old computer recently fell into my lap (Dell Latittude D610), and since I've always loved Ubuntu (and am not willing to give up Win 7 on my desktop) I decided I would install it on this thing. After going through a few distros of Ubuntu and Ubuntu Studio I realized my i915 chipset is pretty much hated by Linux, I eventually stumbled on Xubuntu, which appears to be quite a bit more leight-weight than other distros. (Plus the Xfce enviroment is nice xD)

Anyway I should probably stop getting off topic. I installed Xubuntu 12.10 first and since the wireless card was not recognized I plug in this old PCI express wifi card I had lying around and it read that one just fine so I could have it connected to the internet during install. So anyway the disc failed during install.

This time I decided I would just get the alternative as it as smaller and this peice only has a 30GB hard drive anyway. So I got Xubuntu Alternate 12.04 (or something like that) and it didn't seems to have any trouble finding drivers for my hardware (graphics included), it had even found my internal wireless card (along with the express card, which was still plugged in). Anyway by the time it was all set up I realized it did infact set up a driver for my internal wireless card, but now it's using the PCI express card and I couldn't figure out how to get it to use my internal card! (which I would prefer as it gets a better siginal and isn't all bulky sticking out of the side).

After messing around with it for some time I figured I found a README from Broadcam for this specific driver. It explained that if you go into the Package Manager, reinstall the package, than restart your computer and it says it should read just fine. Anyway I found the package and started to re-install it, after a while I noticed it had frozen when it was nearly done. I waited like 45 min. and finally I just closed out of it.

So now whenever I open Synaptic it display's the following message:
[I]
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/I]

So naturally I assumed that I would open Terminal and run *dpkg --configure -a*
I've also tried running it with *sudo* at the beginning and as a superuser, no matter what it comes out with the same result:

[I]root@ubuntuKris:/home/kris# sudo dpkg --configure -a
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu0.0.1) ...
Removing old bcmwl-6.20.155.1+bdcom DKMS files...

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.20.155.1+bdcom
Kernel:  3.2.0-38-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-38-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod..........

DKMS: uninstall completed.

------------------------------
Deleting module version: 6.20.155.1+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
Building only for 3.2.0-38-generic
Building for architecture i686
Building initial module for 3.2.0-38-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-38-generic/updates/dkms/

depmod....

DKMS: install completed.

[/I]After this it doesn't do anything, and doesn't allow me to input anymore commands (although I can still type letters in the console, if that's relevant). Although it appears to me it successfully reinstalled the driver...

Now, when I try to open Synaptic I get this message:

This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first.

(and yes, I've tried finding another app, but I can't figure out what it's referring to, if anything)

Now whenever the computer is rebooted it reverts back to:

[I]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/I]

And it's sort of an endless cycle... Trying to fix my wireless card and I end up doing this, and I wanted to post something here before trying anything else that will potentially mess it up even more. Sorry if this is too much info I just wanted to explain in detail in hopes that someone that knew what they were doing would be able to tell what I'm doing wrong...
Thanks in advance...

---

### Post by tgalati4 on 2013-03-15
```
sudo apt-get check
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

Reboot and see what happens.

---

