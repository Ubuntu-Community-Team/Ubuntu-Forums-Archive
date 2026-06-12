---
title: "How to add disk #2"
date: 2006-10-31
forum: General Help
---

### Post by jrohde on 2006-10-31
Hi,

I have just installed Edgy on my Fujitsu-Siemens Scaleo H, that is born with two harddisks.

Now I wan't to format and mount the SDB disk. How do I do that, and where can I find a suitable howto? I have been searching, but no luck.

Thanks,

Jakob

---

### Post by Ramses de Norre on 2006-10-31
Add a line for it in fstab, if you give us some info (sudo fdisk -l; cat /etc/fstab; desired mountpoint) we can tell you which line to insert.

---

### Post by jrohde on 2006-10-31
Hi,

It's the fdisk part and mkfs (?) part I was interested in.

But now you mention it, I have noticed a different syntax in fstab. How does this work?

Jakob

---

### Post by matthewstory on 2006-10-31
well . . . if you want to make it one big partition:

fdisk /dev/sdb

Now you'll be inside of fdisk

n

this creates a new partition

p

for primary partition

1

will be the number of the disk

Hit enter, to start at the beginning, and enter again to stop at the end.

Then hit w to write and exit.

Once that's done you need to crete the file system:

assuming you want ext3:

mke2fs -j /dev/sdb1

And Wham! you're good to go.  If you want this to automount at boot time you'll need to add a line to your /etc/fstab file:

otherwise you can just mount that bad mother:

mount /dev/sdb1 /path/to/mount

enjoy!

---

### Post by matthewstory on 2006-10-31
oops been using debian for too long . . . you will of course need to use sudo to run both fdisk and also mke2fs . . . my bad.

---

### Post by Ramses de Norre on 2006-11-01
To format it I'd use gparted or qtparted, it's a lot easier. And yes fstab changed a bit but you can still add disks with the old syntax too, just add them to the end.

---

