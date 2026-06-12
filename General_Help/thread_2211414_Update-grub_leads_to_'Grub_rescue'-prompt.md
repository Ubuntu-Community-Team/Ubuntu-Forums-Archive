---
title: "Update-grub leads to 'Grub rescue'-prompt"
date: 2014-03-15
forum: General Help
---

### Post by Tristan_Williams on 2014-03-15
I had Ubuntu studio on /dev/sda and Ubuntu Minimal on /dev/sdb
Grub was installed on /dev/sdb
My main system was Ubuntu Minimal, so I though it would be harmless to remove Ubuntu Studio, and do the "install gentoo from ubuntu" thing.

All went well while installing.

When I was completely done, I issued 'sudo update-grub'

Reboot.

Grub rescue >

Well wtf...

This seems to happen every time I do anything similar to what I just did.

Why can't grub work the right way?

Similar story:
Had same layout as before, except grub was on /dev/sda with Ubuntu Studio.
Grub would show Ubuntu studio and Ubuntu Minimal

Removed Ubuntu Minimal, went back to Studio, and updated grub.

Rebooted again and it still showed Ubuntu minimal.

It also refuses to realize when I install or remove a kernel...

Anyone care to explain why grub does this?

---

### Post by slooksterpsv on 2014-03-16
Where is grub sda or sdb? If you try booting directly from the second drive, does it work?

---

### Post by r.stiltskin on 2014-03-16
update-grub rewrites /boot/grub.cfg to reflect any changes you make to /etc/default/grub and the scripts in /etc/grub.d but it doesn't change the Grub Stage 1 and 1.5 code in and immediately following the boot sector of your disk.  That code looks for Grub Stage 2 code in the partition from which you installed grub.  So, for example, if you installed Grub from Ubuntu Studio, Grub Stage 1.5 is looking for its Stage 2 code in your Ubuntu Studio partition, but that code is no longer there after you delete Ubuntu Studio.

So update-grub isn't enough.  You should run 
```

sudo update-grub
sudo grub-install /dev/sdX
## replace X with a or b -- representing the boot drive specified in your bios setup
```
from whichever system (Ubuntu Minimal or Gentoo) contains the grub configuration files that you want to use.

---

### Post by Tristan_Williams on 2014-03-16
> **r.stiltskin said:**
> 
So update-grub isn't enough.  You should run 
```

sudo update-grub
sudo grub-install /dev/sdX
## replace X with a or b -- representing the boot drive specified in your bios setup
```
from whichever system (Ubuntu Minimal or Gentoo) contains the grub configuration files that you want to use.

Thanks, that fixed it.

---

