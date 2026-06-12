---
title: "Dual boot - want to change mount point of Windows partition"
date: 2012-11-08
forum: General Help
---

### Post by Paperypip on 2012-11-08
I'm running a Linux/Windows dual boot system and within Linux the Windows partition's mount point is named in an ugly way (specifically: /media/*my name here*/66FECB6AFECB30DB). How do I change it? I want to make it easier to make hard-links to directories on that partition.

I've been pointed towards fstab but I don't understand what I'm looking at when I check that file out:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=cffff423-9671-4941-b2cb-a39b9950c1c1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2d0d506f-dd93-440a-87be-91f82a63f553 none            swap    sw              0       0

```

I was thinking maybe I could just simply change things around using GParted but I guess not.

---

### Post by carl4926 on 2012-11-08
Windows will not be in fstab, not from a normal install.

If you want a nicer feel to this, you can add it to fstab, but you might try first, just adding a volume label to the windows partition using gparted.

---

### Post by mikewhatever on 2012-11-08
Why is that an ugly way? The long number (66FECB6AFECB30DB) is likely the Windows partition UUID, which uniquely identifies the partition. I really don't think anything is wrong with it.

PS: You are right, Gparted has nothing to do with it.

---

### Post by Wim Sturkenboom on 2012-11-08
It's indeed ugly. Boot into windows and give your Windows disks / partitions decent names (label). My Win7 partition is labeled Win7, my WinXP partition is labeled WinXP and my WinXP data partition is called WinXPData. And those are the names that show in the filemanager.

---

### Post by oldfred on 2012-11-08
Easy way to label partitions
System> Admin.> Disk Utility
Or with Unity just Disk Utility

to see labels:

Shows all partitions labels & UUIDs
sudo blkid -c /dev/null -o list

Shows labels:
ls -l /dev/disk/by-label/

---

