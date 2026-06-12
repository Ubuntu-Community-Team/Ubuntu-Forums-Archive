---
title: "Changing order of hard drives - how to adapt linux to boot?"
date: 2008-04-15
forum: General Help
---

### Post by ZeleniZub on 2008-04-15
Hi,

I have repositioned my hard drives lately, when re-packing the PC, which made ubuntu loose track of where which filesystem is.

This resulted in error messages like: can't mount /, since /dev/hdb doesn't contain file/folder XY (makes sense, since its on another drive, that came in its position).



Is there an easy way to change paths where ubuntu looks for filesystems? (there is not an option for that in BIOS, too old I guess)

/etc/fstab came to my mind, but I guess that is too late in the boot sequence. It should have to be somewhere in GRUB settings...


Thanks 
Nikola

---

### Post by forestpixie on 2008-04-15
In grub menu.lst tells the system where to look - there are references in your menu.lst to hd(0,1) etc - this would be drive 1 and second partition.

It might be easiest to reinstall grub - couple of ways I know of - you can use your buntu livecd - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

alternatively you couan use supergrub - download, burn as an iso and boot with it
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by jocko on 2008-04-15
> **ZeleniZub said:**
> Hi,

I have repositioned my hard drives lately, when re-packing the PC, which made ubuntu loose track of where which filesystem is.

This resulted in error messages like: can't mount /, since /dev/hdb doesn't contain file/folder XY (makes sense, since its on another drive, that came in its position).



Is there an easy way to change paths where ubuntu looks for filesystems? (there is not an option for that in BIOS, too old I guess)

/etc/fstab came to my mind, but I guess that is too late in the boot sequence. It should have to be somewhere in GRUB settings...


Thanks 
Nikola

Try this:
In the grub menu (hit esc before grub tries to load the kernel), select a line that starts with"root"and hit "e" to edit the line. It probably look like this:
```
root            (hd0,0)
```Try changing (hd0,0) to (hd1,0), press enter and then "b" to try to boot.
If it works you should be able to boot all the way, but the change is only temporary.
To make it permanent:```

gksudo gedit /boot/grub/menu.lst
```Find a line that says:
```
# groot=(hd0,0)
```and change to ```
# groot=(hd1,0)
```Then to update grub to use the new setting:```

sudo update-grub
```

---

