---
title: "E: dpkg was interrupted..."
date: 2014-09-14
forum: General Help
---

### Post by edison23 on 2014-09-14
Hi,
I have a strange problem with my brand new installation of Ubuntu 14.04 (and I had same problem with brand new install of Mint, too). While trying to install proprietary drivers for wifi adapter on my old laptop Acer Aspire 3692, the installation got stuck and didn't finish. When I then tried to install some other software later I got error:
```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
```
So I tried to do as told and got **segmentation fault**. Happens even after restart of OS.
Now I can't install new software or update and I still can't use wifi. 
I need an advice what to do.

Thanks

---

### Post by pissedoffdude on 2014-09-14
Try doing a ```
sudo apt-get -f install 
```

If that takes care of the issue, maybe try installing the firmware your wireless card needs via the command line:```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get update
sudo update-pciids
sudo apt-get install linux-firmware-nonfree

```

Then reboot.  And don't worry if you get an error after running the first apt-get purge command since you might not have that package installed

EDIT: If the apt-get -f install doesn't fix it, you might have a corrupted cache, so clear it and check again:
```
sudo rm /var/cache/apt/*.bin
sudo apt-get update
sudo apt-get uprade
```

---

### Post by ian-weisser on 2014-09-14
It would sure help to know exactly when during the config process the segfault occurs, and which application is segfaulting.

Any chance you can copy-and-paste a complete terminal session output?

---

### Post by edison23 on 2014-09-18
I was away for a few days, will try what you suggested now, thanks

---

### Post by edison23 on 2014-09-18
So, I've tried what you've suggested - doesn't look it helped, here's the output:
```

edison23@edison23-Aspire-3690:~$ sudo apt-get -f install
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
edison23@edison23-Aspire-3690:~$ sudo rm /var/cache/apt/*.bin
rm: cannot remove ‘/var/cache/apt/*.bin’: No such file or directory

```

And if I do dpkg --configure -a as suggested:
```

edison23@edison23-Aspire-3690:~$ sudo dpkg --configure -a
Setting up bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu2) ...
Removing old bcmwl-6.30.223.141+bdcom DKMS files...

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.30.223.141+bdcom
Kernel:  3.13.0-32-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-32-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.........

DKMS: uninstall completed.

------------------------------
Deleting module version: 6.30.223.141+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-6.30.223.141+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.13.0-32-generic
Building for architecture i686
Building initial module for 3.13.0-32-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-32-generic/updates/dkms/

depmod....

DKMS: install completed.
 Segmentation fault

```
After this, even wired internet connection breaks.
Do I miss something? What should I post to help you determine where the problem is?
Thanks a lot.

---

### Post by edison23 on 2014-09-18
Ok, obviously, I didn't google enough. Found an answer here: [http://ubuntuforums.org/showthread.php?t=2240241](http://ubuntuforums.org/showthread.php?t=2240241)
The solution was:
```
sudo dpkg -P bcmwl-kernel-source
```
restart
```
sudo apt-get install firmware-b43-installer
```

For anyone else having this problem, be advised, that this is probably very much wifi-adapter dependent, so think before typing. And dont let the wifi driver be installed by OS automatically.
 If you want details they're in the original thread linked above.

A/w, thank you, Ubuntu forums!
edison

P.S. Could some OP mark this as [SOLVED], please? Apparently, I can't.

---

### Post by Bashing-om on 2014-09-18
edison23; Great !

Appreciate that you provided your solution ( and the appropriate admonition ) .
To mark the thread solved : top of post -> thread tools

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

