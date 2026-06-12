---
title: "Grub - /bin/sh: can't access tty; job control turned off"
date: 2007-01-27
forum: General Help
---

### Post by Gorlist on 2007-01-27
Hi! right im running two harddrives, one with Windows XP installed the other Ubuntu (both SATA) - when I orignally installed Ubuntu I unplugged the Windows drive so each system has its own boot loader.

Following another thread ive set Ubuntu as the primary drive and edited the Grub loader to include Windows XP - all works fine, 

The Grub Loader loads & I can select Windows or Ubuntu, Windows will load fine no problems, though when I select Ubuntu it comes up with:

[B]/bin/sh: can't access tty; job control turned off 

(along with a number of errors above regarding to loading something)[/B] 

Now if I un-plug the Windows drive and try to load again then select Buntu it will load fine...

Any suggestions?

---

### Post by confused57 on 2007-01-27
> **Gorlist said:**
> Hi! right im running two harddrives, one with Windows XP installed the other Ubuntu (both SATA) - when I orignally installed Ubuntu I unplugged the Windows drive so each system has its own boot loader.

Following another thread ive set Ubuntu as the primary drive and edited the Grub loader to include Windows XP - all works fine, 

The Grub Loader loads & I can select Windows or Ubuntu, Windows will load fine no problems, though when I select Ubuntu it comes up with:

[B]/bin/sh: can't access tty; job control turned off 

(along with a number of errors above regarding to loading something)[/B] 

Now if I un-plug the Windows drive and try to load again then select Buntu it will load fine...

Any suggestions?
A forum search didn't really come up with any definitive solutions for this error, but maybe if you can post some info, it "might" help.  I assume you're able to boot to Windows, with both drives connected, by selecting the Windows drive to boot first in bios.

With both drives connected, you might want to boot up with the live cd, open a terminal, enter:
```
sudo fdisk -l
```
The -l is a small "L".

Then shutdown, disconnect your Windows drive, boot up Ubuntu, open a terminal, and post the outputs of:
```
cat /boot/grub/menu.lst
```
just post the section near the bottom of the file for the entries to boot Ubuntu & Windows

then:
```
cat etc/fstab
```

also, may want to run sudo fdisk -l again & post results

It'll take a little effort, but if you can post the above, it "may" shed some light on what the problem could be...no guarantees, but worth a try.

---

