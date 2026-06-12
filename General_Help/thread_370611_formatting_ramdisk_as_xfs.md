---
title: "formatting ramdisk as xfs"
date: 2007-02-25
forum: General Help
---

### Post by Ptero-4 on 2007-02-25
Hi. I`m creating a ramdisk in my computer. Currently it`s a 2MB ramdisk and I want to format it as xfs, but the mkfs.xfs command doesn`t allow me to do it (I pass it the -f option to force it to format it), it says something about the blocksize and I wanted to know. How do I do to format a ramdisk that have a size of 2MB using the xfs filesystem?

---

### Post by dcstar on 2007-02-25
> **Ptero-4 said:**
> Hi. I`m creating a ramdisk in my computer. Currently it`s a 2MB ramdisk and I want to format it as xfs, but the mkfs.xfs command doesn`t allow me to do it (I pass it the -f option to force it to format it), it says something about the blocksize and I wanted to know. How do I do to format a ramdisk that have a size of 2MB using the xfs filesystem?

Maybe a disk a bit bigger than a 1.44 MB floppy is just too small for that filesystem?

---

### Post by Azakus on 2007-02-26
XFS has a minimum size of 32MB. For that 2MB RAM disk, I'd try FAT16. If you went with something bigger, say 8MB, you could use ext2 or ext3.

---

### Post by Ptero-4 on 2007-02-28
Thanks Azakus. But unfortunatelly I tried both FAT16/FAT32 and they won`t get formatted, there`s an error about ¨default¨ something followed by a fractionary number.

---

