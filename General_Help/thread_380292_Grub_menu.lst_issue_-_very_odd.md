---
title: "Grub menu.lst issue - very odd"
date: 2007-03-09
forum: General Help
---

### Post by musther on 2007-03-09
I've finally convinced an old desktop to take Edgy, but Grub's options are wrong.

The grub entry is this:

```
title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot
```

Note that root is hd0,0 and root on the kernel line is hda1.  That's wrong, root is actually hda2 and hence the machine wont boot.  So when grub loads, I go into edit mode and change hda1 to hda2, the system boots nicely.  So I opened up menu.lst in gedit to change the settings, and found the entry in menu.lst says:

```
title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot
```

I was very puzzled, so I tried changing it to something random like hdb3, saved the file and rebooted.  Grub seemed exactly the same, but when I booted again my changes were still there.  

In short, nothing I do to /boot/grub/menu.lst makes any difference to what actually shows up in grub when booting.  I've tried removing all the entries from menu.lst, I've changed them, nothing makes any difference - it's like grub is getting its config from somewhere else.

Anyone got any ideas?

---

### Post by Kateikyoushi on 2007-03-09
Might sound strange but, did you try to search for another menu.lst ?

---

### Post by lloyd_b on 2007-03-09
> In short, nothing I do to /boot/grub/menu.lst makes any difference to what actually shows up in grub when booting. I've tried removing all the entries from menu.lst, I've changed them, nothing makes any difference - it's like grub is getting its config from somewhere else.

Are you running "sudo grub-install /dev/hda" after making the changes?  Grub does not (AFAIK) actually read this file each time you boot - it's just read by grub-install to reconfigure grub.

Lloyd B.

---

### Post by llamakc on 2007-03-09
Unlike LILO you can edit the menu.lst file and the changes will be seen.

Does the OP dual-boot or have more than one version of Linux installed on this machine?

What are the contents of /boot/grub? And the output of `fdisk -l /dev/hda`?

Also, the first entry for root (hd0,0) refers to the root of GRUB, not your filesystem. The second entry is where / is mounted.

Try changing JUST the second entry for your filesystem and see if that works. It should.

---

### Post by moore.bryan on 2007-03-09
> **musther said:**
> 
```
title        Ubuntu, kernel 2.6.17-11-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash
initrd        /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot
```
```
title        Ubuntu, kernel 2.6.17-11-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro quiet splash
initrd        /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot
```
*it is changed... look at it again.  your first entry with hda1 is root (hd0,0) and your second with hda2 is root (hd0,1)... that's what it should be.  maybe i don't understand your problem...*

---

### Post by musther on 2007-03-09
Thanks for the help, I figured it out.  There's another drive in this machine, hdd (not hard disk drive, hdd as in hda or hdb), with an old grub installation on it, it was that which was loading, had to change the priority of booting the IDE drives in the bios.  Confusing, but simple.

Thanks again

---

### Post by moore.bryan on 2007-03-10
*glas to hear your got it working... happy ubuntu-ing~*

---

### Post by strabes on 2007-03-10
You have to actually edit the /boot/grub/menu.lst file for your changes to be permanent. Editing the boot options within grub only affect it once.

---

