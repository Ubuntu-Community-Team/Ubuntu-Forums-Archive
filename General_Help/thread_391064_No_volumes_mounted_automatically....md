---
title: "No volumes mounted automatically..."
date: 2007-03-22
forum: General Help
---

### Post by gejr on 2007-03-22
Hey there,, I'm a pretty new linux user so every suggestion is good! 
I have a Ubuntu Edgy install here that doesn't mount the other harddisks/partitions automatically. Isn't Ubuntu supposed to do this automatically? As far as I remember I could find the NTFS partitions on the desktop whether I liked it or not:)

I have an install here now, 2 disks with 80gb each. Ubuntu is installed on one of them, but I have to mount the other manually to access all my mp3's, videos etc. The other disk is partitioned with NTFS, so now I have to mount it manually every time I start Ubuntu with mount -t ntfs /dev/sdb1 /mnt/windisk/

Can't figure out how to make this happen automatically either, because mount needs sudo command in front of it and those commands can't be put in Sessions/Startup programs..

I hope somebody understand the problem and give me some help :)

---

### Post by Muzik83 on 2007-03-22
Hey,

You want to take a look at the file /etc/fstab  This file controls the drives mounted on boot.

You will probably want to add something like this to it:
/dev/sdb1 /mnt/windisk ntfs defaults 0 0

For further information, you can look at the man page for fstab
man 5 fstab

Hope this helps

-sean

---

### Post by gejr on 2007-03-23
Thanks for your reply.. and I apologise for going to bed last night:) However I tried this morning. I have installed the ntfs-3g package, and would like to mount with that. I tried adding:

/dev/sdb1 /mnt/windisk ntfs-3g defaults 0 0

Didn't work however. Isn't this way supposed to work with ntfs-3g?

---

