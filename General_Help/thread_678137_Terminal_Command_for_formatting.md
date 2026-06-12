---
title: "Terminal Command for formatting"
date: 2008-01-25
forum: General Help
---

### Post by ryanlhjess on 2008-01-25
Good day, 

Im looking for the command to format..

IE, im looking to format Hda7....

---

### Post by logos34 on 2008-01-25
format as what?  ntfs? ext3? fat32? reiserfs?

---

### Post by ryanlhjess on 2008-01-25
ext3

---

### Post by logos34 on 2008-01-25
**sudo mkfs.ext3 /dev/hda7**

or

sudo mke2fs -j /dev/hda7

---

### Post by ryanlhjess on 2008-01-25
One more question....how do i unmount a volume?

---

### Post by ryanlhjess on 2008-01-25
I think i figured it out


sudo umount /dev/hda7

---

### Post by Zwack on 2008-01-25
or 
sudo mkfs -t <type> <file system>

so you could use
sudo mkfs -t ext3 /dev/hda7
for an ext3 filesystem on /dev/hda7

And yes 

sudo umount /dev/hda7
or
sudo umount /mountpoint
should work.

Z.

---

