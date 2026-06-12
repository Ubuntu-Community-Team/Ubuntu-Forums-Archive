---
title: "Mounting with fstab causes hang on boot but with mount command no issues"
date: 2014-07-24
forum: General Help
---

### Post by excetara2 on 2014-07-24
I have an Asus UX301 (dual-boot raid 0 system) and I am having issues with adding a ntfs drive to the fstab in Ubuntu. Whenever I add it I get a hang at boot or the error below when I reload the fstab file (mount -a):

mount: wrong fs type, bad option, bad superblock on /dev/mapper/isw_djifjjhhid_ASUS_OS7,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

My fstab is as simple as this:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
# / was on /dev/md126p5 during installation
UUID=d4f9468b-a655-491f-b0d1-c4322fae9550 / ext4 errors=remount-ro 0 1
# /boot/efi was on /dev/md126p2 during installation
#UUID=A262-7052 /boot/efi vfat defaults 0 1
# /home was on /dev/md126p6 during installation
UUID=39f3f991-5c9c-4a3c-9e64-b4ca39837cb4 /home ext4 defaults 0 2
# swap was on /dev/md126p8 during installation
UUID=c674745a-934a-4730-bdfb-267fda2fcb78 none swap sw 0 0
UUID=A262-7052 /boot/efi vfat defaults 0 1
UUID=691F1BB67AE18A58 /mnt/data ext4 defaults 0 2


Any ideas as to what is going on?

---

### Post by Bucky Ball on 2014-07-24
What have you changed/added to the fstab manually?

All I can think is that you have a UUID wrong. Open the /etc/fstab in a terminal, open another terminal and issue 'sudo blkid'. Compare the UUIDs and make sure they are correct and correspond.

Not sure about this:

```
 UUID=39f3f991-5c9c-4a3c-9e64-b4ca39837cb4 /home ext4 defaults 0 2
```

Why is it not the same at the end as your / partition?

```
UUID=d4f9468b-a655-491f-b0d1-c4322fae9550 / ext4 errors=remount-ro 0 1
```

Perhaps change to:

```
 UUID=39f3f991-5c9c-4a3c-9e64-b4ca39837cb4 /home ext4 errors=remount-ro 0 1
```

... unless you have altered it for a specific reason.

---

### Post by excetara2 on 2014-07-24
It's actually a solid state drive and ntfs so that was the issue. I just had to change the ext4 to ntfs.I can't believe I made that mistake.

---

### Post by Bucky Ball on 2014-07-24
Ah! Easy fix. 

Good luck. ;)

---

