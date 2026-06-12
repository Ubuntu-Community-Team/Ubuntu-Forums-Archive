---
title: "BootLoader Woes (GRUB)"
date: 2007-06-04
forum: General Help
---

### Post by iceportal on 2007-06-04
I've had 7.04 installed on my system for quite some time now, but a friend of mine was going to try Debian 4.0, so I wanted to install it on my computer as well. Figured I'd dual-boot, but I wanted to keep my Ubuntu bootloader, so that if I ever switched to another OS I could just reconfigure one instead of reinstallling every time.

So I chose, during Debian setup, to NOT install a bootloader, thinking I'd just add Debian to the bootloader I already have.

Debian told me that the installlation was located at /dev/hda3 and that the root was /vmlinuz and /dev/hda3.

So... I'm lost as to how to add Debian to boot on my machine.

I know where the grub info is located (/boot/grub/menu.lst) and I've backed up and edited it, but I just can't seem to get the proper parameters.

Any ideas?

---

### Post by x64Jimbo on 2007-06-04
There are some good tutorials on setting up Grub out there. Searching google for "grub menu.list" returned this as the second result:
[http://ubuntuforums.org/showthread.php?p=1319395](http://ubuntuforums.org/showthread.php?p=1319395)

---

### Post by 5-HT on 2007-06-04
You'll need to poke around you Debian /boot to find out what your kernel (seems to be the  normal 'vmlinuz' from your post) and initial ramdisk (if used) are called. If you're not using an initial ramdisk you can omit the 'initrd' line. The 'root' line of the entry will be (hd0,2) for hda3.

Something like the following, after editing for your proper kernel and initrd path, will work:

```
title  enter_what_ever_you_wish_grub_to_call_the_entry
root   (hd0,2)
kernel /boot/vmlinuz root=/dev/hda3 ro
initrd /boot/initrd.img
```

---

