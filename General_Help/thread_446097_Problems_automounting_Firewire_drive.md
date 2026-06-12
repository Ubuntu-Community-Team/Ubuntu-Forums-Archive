---
title: "Problems automounting Firewire drive"
date: 2007-05-16
forum: General Help
---

### Post by hypersire on 2007-05-16
If I boot up with my firewire drive turned on, it is automounted and an icon appears on the desktop. If I turn the drive off, icon disappears. Turn the drive back on, icon reappears. Everything works as it should.

The problem is if I boot up my computer with the firewire drive turned off. If I turn it on after booting, nothing happens. No icon appears on the desktop. I tried to manually mount using "mount /dev/sda" but it says "mount: can't find dev/sda in /etc/fstab or /etc/mtab". I thought fstab was only supposed to contain information about permanently attached devices?

I followed the instructions found here:

[http://ubuntu-tutorials.com/2006/12/06/how-to-always-mount-removable-drives-in-the-same-place-ubuntu-6061-610/](http://ubuntu-tutorials.com/2006/12/06/how-to-always-mount-removable-drives-in-the-same-place-ubuntu-6061-610/)

on always automounting a drive in the same location. I created the file "/etc/udev/rules.d/10-local.rules" and added my firewire drive to it but it didn't make a difference. I tried running "sudo /etc/init.d/udev restart" after turning the drive on but nothing. The only way for me to use the drive is if I boot up with it on, but I would like to be able to plug it in after the fact and have it automounted and an icon to appear on my desktop.

Any suggestions?

TIA!

---

### Post by hypersire on 2007-05-16
Anyone?

---

