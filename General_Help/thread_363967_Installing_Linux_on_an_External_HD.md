---
title: "Installing Linux on an External HD"
date: 2007-02-17
forum: General Help
---

### Post by kevCast on 2007-02-17
I was wondering if it was possible to install Ubuntu on an external HD. Not a regular external HD, more like a Creative Zen Vision M. It's got up to 32GB of space that you can dedicate to putting into the hardrive, the problem is I tried installing it on it before, and it ruined my PC.

Any ideas?

---

### Post by bernied on 2007-02-17
I've put slax onto usb flash drives a few times. There are howtos out there.
I've also got a device like yours, though mine is a Zen Micro and I've only got 1GB for 'data storage'. The question is whether the device can be booted from, unless you would keep the bootloader on the PC - if you did that you'd only be able to run it from that PC. 

One way to test this might be to see if grub can see the device. So, put an empty file with a specific name in the device, then see if grub can find that file at boot time.

This would not be conclusive, but it would at least mean that grub can get to the device, so maybe you can boot from it. I might try it on mine, see what happens.

---

### Post by bernied on 2007-02-17
I just had a look at mine with fdisk, doesn't look promising as it's not behaving like a proper disk. What output do you get?
```
root@shinym:/mnt# fdisk /dev/sde

Command (m for help): p

Disk /dev/sde: 1073 MB, 1073741824 bytes
34 heads, 61 sectors/track, 1011 cylinders
Units = cylinders of 2074 * 512 = 1061888 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   ?      901530      982865    84344761   69  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(68, 13, 10) logical=(901529, 3, 37)
Partition 1 has different physical/logical endings:
     phys=(288, 115, 43) logical=(982864, 15, 36)
Partition 1 does not end on cylinder boundary.
/dev/sde2   ?      820405     1721987   934940732+  73  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(371, 114, 37) logical=(820404, 25, 61)
Partition 2 has different physical/logical endings:
     phys=(366, 32, 33) logical=(1721986, 32, 30)
Partition 2 does not end on cylinder boundary.
/dev/sde3   ?           2           2           0   74  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(371, 114, 37) logical=(1, 8, 12)
Partition 3 has different physical/logical endings:
     phys=(372, 97, 50) logical=(1, 8, 11)
Partition 3 does not end on cylinder boundary.
/dev/sde4         1391361     1391386       26207+   0  Empty
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 0) logical=(1391360, 8, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(1391385, 17, 40)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```

---

### Post by carrie.peary on 2007-02-17
I succesfully got mine to install on my externall HDD (although deleted once I installed it on my laptop) with no problems following this how-to: [http://ubuntuforums.org/showthread.php?t=80811&highlight=external+harddrive+install](http://ubuntuforums.org/showthread.php?t=80811&highlight=external+harddrive+install)

---

### Post by bernied on 2007-02-17
Well it works on the Creative Zen Micro. I'm writing this from a copied slax install running on the zen micro. 
I had to repartition the 'disk' manually using fdisk - I actually created a new partition table because it didn't seem to have one, then created three partitions, one for data (vfat - 760MB), one for booting grub (ext2 - 3MB) and one for the slax install (ext2 - 250MB). With a bit of luck, once I've formatted it right, the data partition will show up nicely on Windows machines.

So if it can be done with slax, it can be done with ubuntu.

In my opinion though, it may not be a good idea. Slax runs well, because it is designed as a very small OS to run mainly (or entirely) in memory. But the ubuntu install is huuuge in comparison, and you'd be doing a lot of reading and writing through usb. So it might be very slow. It is very appealing idea though, to have a custmised ubuntu install in your pocket to demonstrate to your geeky friends.

---

### Post by bernied on 2007-02-17
I think that you could probably use [that](http://ubuntuforums.org/showthread.php?t=80811) howto linked to by carrie.peary. But if your machine is like mine, then you might have to partition the 'disk' using fdisk or maybe gparted first. Or maybe not.

And, in case you were worried (because I was) the zen micro still works as a music player.

---

