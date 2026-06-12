---
title: "NTFS-&gt;ext3"
date: 2008-04-04
forum: General Help
---

### Post by sNNooPY on 2008-04-04
is it possible to do a NTFS->ext3 conversion without losing your files?

---

### Post by zvacet on 2008-04-04
I don´t think so,because when you format drive you delete files.

---

### Post by ZarathustraDK on 2008-04-04
If you've got enough space then you can defrag your ntfs-drive, then resize it to free up space for a new partition, make the new partition ext3, install Ubuntu with ntfs-3g support, move the files from the ntfs-partition to the ext3 partition, delete the ntfs-partition, and then resize the ext3-partition to use all of the harddisk space.

Or you could use an eksternal disk and copy over your files from the ntfs-partition, but that's too easy :)

---

### Post by articpenguin on 2008-04-04
not possible.

You can convert ext2 to ext3. Ext3 is just ext2 with a journal.

---

