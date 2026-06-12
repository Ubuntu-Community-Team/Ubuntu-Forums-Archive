---
title: "btrfs, raid1 and fstab..."
date: 2014-01-28
forum: General Help
---

### Post by whoop on 2014-01-28
I am experimenting with btrfs with raid1 on a virtual machine. I want to see if a full raid1 btrfs system is possible. I Installed ubuntu server on a single harddisk with one partition / btrfs (/dev/sda) just to test. Then I added a second harddisk (/dev/sdb) created a btrfs filesystem on it and then I ran:

```

mount /dev/sda1 /mnt
btrfs device add /dev/sdb1 /mnt
btrfs balance start -dconvert=raid1 -mconvert=raid1 /mnt
grub-install /dev/sdb

```

The above commands are to create the raid1 array with the two harddisks and the grub command was to be able to boot from both harddisks...
I am under the impression that it works: I can boot from both disks and both disks show having the same amount of data on it (viewed with gparted on livecd)

I have no idea if this is a proper way to do this. I come from mdadm logic so my method may reflect this... Also I am unsure how to edit /etc/fstab in order to reflect these RAID1 changes. Currently my /etc/fstab looks like this (which can't be right, although it seems to be working):
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=3de7d26c-a217-4797-aa29-84bcf8a811fe /               btrfs   defaults,subvol=@ 0       1
# /home was on /dev/sda1 during installation
UUID=3de7d26c-a217-4797-aa29-84bcf8a811fe /home           btrfs   defaults,subvol=@home 0       2

```

thanks...

---

### Post by whoop on 2014-01-28
After further examination blkid gives me this:
```

/dev/sda1: UUID="3de7d26c-a217-4797-aa29-84bcf8a811fe" UUID_SUB="be59e5c3-768b-4768-b448-37cf98fe6ef0" TYPE="btrfs" 
/dev/sdb1: UUID="3de7d26c-a217-4797-aa29-84bcf8a811fe" UUID_SUB="d07a4553-5f40-4bc3-9820-df837c02f430" TYPE="btrfs" 

```

So both drives have the same UUID, so maybe /etc/fstab is correct after all?

---

