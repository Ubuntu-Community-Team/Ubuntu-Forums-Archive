---
title: "Live distros in external usb disk"
date: 2008-05-11
forum: General Help
---

### Post by geo909 on 2008-05-11
Hello everybody,

I have an external usb 500gb hard disk.I want it for backup purposes mainly but I want to do another thing with it:

I would like to dedicate 1 GB of my disk (a partition or several ones if needed) for some live distros, install a bootloader too (Grub for example) and make my disk bootable under various options (Puppy linux, gParted live, Clonezilla, trinity etc.).

 All of the distros mentioned above, have the option to be installed on a USB stick. So what I am willing to do is to have them all together in a small partition(s) of my external disk. The main partition will be a 499 GB one and will be for storage purposes. No live tools.

 Anyone, do you have any ideas?

---

### Post by ibuclaw on 2008-05-11
My first leap of faith would be to buy a mag or book with a LiveCD that does this sort of trickery (Linux Bible is a good example, LinuxMag does it from time to time too). And try to work out how everything gels.

Though I'd probably give up that the minute I start.

Alternatively, I would probably look at How-tos for booting LiveCDs on disk.
If I were to do it this way, I would have each in their own separate folders, and then use Ubuntu's grub boot menu to point at the locations of their separate kernels.

ie: Put something like this in your "/boot/grub/menu.lst" file
```

title           Pupply LiveCD
root            (hd1,0)
kernel          /opt/puppy/boot/vmlinuz ro quiet splash rootflags=data=writeback
initrd          /opt/puppy/boot/initrd.img
quiet

title           Gparted LiveCD
root            (hd1,0)
kernel          /opt/gparted/boot/vmlinuz ro quiet splash rootflags=data=writeback
initrd          /opt/gparted/boot/initrd.img
quiet

```

[There are plenty of how-tos out there.]("http://www.google.co.uk/search?hl=en&q=LiveCDs+on+Disk&btnG=Google+Search&meta=")
It's just a case of getting one to work for you.

Regards
Iain

---

