---
title: "unmount filesystem that contains OS"
date: 2014-08-28
forum: General Help
---

### Post by project722 on 2014-08-28
Is it possible to un-mount the FS that contains the OS while the system is booted without causing problems? For instance if I wanted to run fsck on it without rebooting?

---

### Post by ajgreeny on 2014-08-28
Can't be done, so forget about doing it that way.

You can boot to a live system and then run ```
sudo e2fsck /dev/sdx#
``` where sdx# is the root partition of the OS you want to check.
Alternatively you can run command ```
sudo touch /forcefsck
``` in the running OS and then reboot; a filesystem check will be carried out as you reboot.

---

### Post by project722 on 2014-08-29
Ok thanks, I just setup a new partition to test with. I created another primary partition and when I went to lay down a FS it threw this error:

sudo mkfs -t ext4 /dev/sda2
mke2fs 1.42.9 (4-Feb-2014)
mkfs.ext4: inode_size (128) * inodes_count (0) too big for a
        filesystem with 0 blocks, specify higher inode_ratio (-i)
        or lower inode count (-N).
I have tried both with an extended partition and a primary partition and get the same error.

---

### Post by project722 on 2014-08-29
problem resolved. Thanks for the help

---

