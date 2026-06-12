---
title: "fstab woes"
date: 2018-02-24
forum: General Help
---

### Post by mickee384 on 2018-02-24
Hi everyone. I was making an addendum to fstab and screwed up the second last line. I was using sudo nano and tried to save the last line using the vi command. The computer still boots, but I think the partition info is now wrong. The error in gparted is: 
[ATTACH=CONFIG]278643[/ATTACH]
The only line that needs fixing is the 2nd last one. Here is the file ```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=065b05a8-1c0e-4c36-9325-c19f1a40dc29 /boot           ext2    defaults        0       2
# /boot/efi was on /dev/sda1 during installation
UUID=7E84-4138  /boot/efi       vfat    umask=0077      0       1
/dev/mapper/ubuntu--vg-root
/swapfile none swap sw 0 0
```

what happened was part of the last line overwrote teh 2nd last. Any help would be appreciated.

---

### Post by Dennis N on 2018-02-24
Device in 2nd-to-last line is same logical volume that's mounted as root on a previous line, so you don't want to try and mount it twice. Put a comment mark (#) at the start of that 2nd-to-last line (so that it's ignored) and see if that fixes any problem when you reboot. You can then delete it - it's imcomplete anyway.

---

### Post by mickee384 on 2018-02-24
Ok, will do this. so should this refer to some other mounted volume?

---

### Post by oldos2er on 2018-02-24
Do you have a swap partition, or a swap file?

---

### Post by mickee384 on 2018-02-24
swap file. Can I use gdisk? I read that I can verify partitions are correct with (p), and use (w) to write the partition table. Will this wipe out my actual partitions? I wouldn't want to do that. But I'm thinking this is meant to fix the GFT while there is a working OS on the main partition? Correct?

---

### Post by mickee384 on 2018-02-27
I fixed it by unmounting and remounting the drives.

---

### Post by rbmorse on 2018-02-27
You still need to remove the second to last line from the fstab.  I don't think it does anything, but it's untidy.

---

