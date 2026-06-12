---
title: "what gives with my harddisk space?"
date: 2007-01-18
forum: General Help
---

### Post by atlfalcons866 on 2007-01-18
it shows my harddrive space wrong what is wrong?

---

### Post by deanjm1963 on 2007-01-18
ext3 by default keeps 5% of your partition/drive space for root use.

---

### Post by atlfalcons866 on 2007-01-18
is the root where all the files locatitions stored like the master file table on NTFS

---

### Post by deanjm1963 on 2007-01-18
root = /  the partition where the system files and programs go. within the root partition, there are other folders, e.g. usr, var, tmp and home if you haven't made a separate home partition.

I remember reading somewhere once, perhaps on here, the reason behind the 5% kept space for root is to stop your drive from filling up and the system being able not to do its thing, e.g. not being able to update, not being able to print because there's no room for printer spool files, no room for tmp files, etc. Keep in mind that when linux first appeared, most people only had one partition, the root partition, and drives were quite small, e.g. 500mb or less, so the system needed to keep a small amount for itself. Think of it as a "buffer space".

Only ext2/ext3 keeps 5% for root use, other file systems such as reiserFS and XFS don't use it.

---

