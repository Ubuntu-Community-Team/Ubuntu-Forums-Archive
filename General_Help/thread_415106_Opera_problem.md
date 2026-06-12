---
title: "Opera problem"
date: 2007-04-20
forum: General Help
---

### Post by ryantmer on 2007-04-20
I've had Opera installed for a few months now on Edgy Eft, without problems. However, two days ago, my shortcut stopped working. I tried running opera from the shell, and I get this:

X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

Segmentation fault (core dumped)

Any ideas/suggestions? I'd really rather not reinstall, as I have a lot of preferences and bookmarks and such that I would rather not lose...

---

### Post by stulesnett on 2007-04-20
Hey, I've encountered the same problems running UBUNTU 6.06.  I did remember there was a Ubuntu update of 3 modules, I don't remember which just prior to Opera stopped respondings.  I have since tried to upgrade to Opera 9.20 and continue to receive an "package installer error " ERROR conflict with package opera"

Any help would appreciated.

Stu

---

### Post by Colonel Kilkenny on 2007-04-20
First problem is fixed by upgrading to newest Opera.

stulesnett, just download deb-package from opera.com and install it with "sudo dpkg -i path/to/operasomething.deb". If it still says something about conflict error, remove opera with "sudo dpkg -r opera" and then try installing it again.

---

### Post by ryantmer on 2007-04-22
I would do the upgrade... but upon downloading the installer from the site (as I don't think I have opera in my sources.list, and if I do, it says 9.10 is the newest version), it tells me that it conflicts with the package "opera". Go figure. Short of doing a removal then a manual install from the site (thereby losing everything I have, which I really, REALLY don't want to do), anything else I could try?

Maybe also worth mentioning that there is no Feisty-specific release of Opera on their site, only goes up to Edgy...


Solved it, never mind. Just adding the opera repository works perfectly :)

---

