---
title: "Easy way to copy grub from one drive to another?"
date: 2013-02-02
forum: General Help
---

### Post by taunnt on 2013-02-02
Hello I'm trying to copy my grub drive to another. What I have tried Clonezilla, it copied everything, but doesn't boot. I have tried to install grub using:

# mke2fs /dev/sdf1
# mount -t ext2 /dev/sdf1 /mnt
# mkdir /mnt/boot
# grub-install --boot-directory=/mnt/boot /dev/sdf1
# umount /mnt

When I get to grub-install --boot-directory=/mnt/boot /dev/sdf1 I get this:

/usr/sbin/grub-bios-setup: warning: File system `ext2' doesn't support embedding.
/usr/sbin/grub-bios-setup: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-bios-setup: error: will not proceed with blocklists.


Is there a better way to copy grub from one drive to another?

---

### Post by arpanaut on 2013-02-02
You are getting that error because you are trying to install into a partition and not to the root of the drive (mbr).

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
is a good read, at the bottom of the page is instruction for moving grub.

---

