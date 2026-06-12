---
title: "Installed new kernel but it doens't go into my menu.lst"
date: 2007-07-03
forum: General Help
---

### Post by Scotty562 on 2007-07-03
I just installed a new kernel via these instructions [http://forums.fedoraforum.org/forum/showthread.php?t=159550](http://forums.fedoraforum.org/forum/showthread.php?t=159550). I followed them to the letter and after I do make install I get this:

make install
sh /usr/src/kernels/linux-2.6.21.5/arch/i386/boot/install.sh 2.6.21.5 arch/i386/boot/bzImage System.map "/boot"
In order to use the new kernel image you have just installed, you
will need to reboot the machine.  First, however, you will need to
either make a bootable floppy diskette, re-run LILO, or have GRUB
installed.

Checking for ELILO...No

GRUB is installed. To automatically switch to new kernels, point your
default entry in menu.lst to /boot/vmlinuz-2.6.21.5

Now when I reboot it's not there! It's driving me nuts! I need this kernel to get my wireless working :(.

---

### Post by lisati on 2007-07-03
Try ```
sudo update-grub
``` and then reboot. Let us know how you get on.....

---

### Post by Scotty562 on 2007-07-03
That worked in a sense. My new kernel is there but it gives a panic error :(. Guess I'll try recompiling things.

---

