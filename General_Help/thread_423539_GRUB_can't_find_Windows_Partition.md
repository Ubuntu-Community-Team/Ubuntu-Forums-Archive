---
title: "GRUB can't find Windows Partition"
date: 2007-04-26
forum: General Help
---

### Post by nemesisrobot on 2007-04-26
Hi, I just installed Ubuntu a few days ago and I'm loving it.  My problem is that while GRUB can correctly load my Ubuntu partition, I can't seem to find my Windows partition.  I just need a little help editing my menu.lst

I've tried changing hd(1,1) to hd(0,1) but that didn't work =/.

here's my menu.lst
```
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=2accecb3-696a-43a9-a3a0-2faf721bfb85 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=2accecb3-696a-43a9-a3a0-2faf721bfb85 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd1,1)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

---

### Post by confused57 on 2007-04-26
You could try rootnoverify, instead of just root.  Your Window's entries in your menu.lst look OK, otherwise.

Do you get any kind of error message when trying to boot Windows?  Is the Ubuntu a new drive you installed & you switched your Window's drive to another controller, i.e. are your jumper settings correct(if IDE), is the hard drive controller in bios enabled?  Any info you can provide about your setup might help.

Added:  Can you boot Windows by changing your hard drive  boot order in bios?

---

### Post by nemesisrobot on 2007-04-26
Thanks for the reply.  My Windows and Ubuntu partitions are on the same drive.  Right after I installed Ubuntu for the first time, I had a problem with GRUB not showing up and booting straight to Windows, so I'm sure that the windows partition is in no way corrupted, just need to point GRUB in the right direction.

---

### Post by confused57 on 2007-04-26
> **nemesisrobot said:**
> Thanks for the reply.  My Windows and Ubuntu partitions are on the same drive.  Right after I installed Ubuntu for the first time, I had a problem with GRUB not showing up and booting straight to Windows, so I'm sure that the windows partition is in no way corrupted, just need to point GRUB in the right direction.

Since you just have one hard drive, you could try an entry similar to this to boot Windows:
```
title		Windows NT/2000/XP
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1
```

```
title		Windows XP Media Center Edition
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1
```

---

### Post by nemesisrobot on 2007-04-26
thanks, that worked for me =)

---

