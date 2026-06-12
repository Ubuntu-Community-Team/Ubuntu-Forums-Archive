---
title: "Size in blocks  v.s. size in bytes in Ext4"
date: 2015-07-05
forum: General Help
---

### Post by ofnuts on 2015-07-05
On an ext4 partition, stat reports:

```

stat -c '%b %B %s %n' *
204800 512 104851585 file1
178584 512 91431059 file2

```
The block group is 4K so eight blocks. 

For file2, (178584*512)-91431059=3949 so the minimum block count has been allocated. But for file1, (204800*512)-104851585=6015, so there is an extra block allocated. In practice I find that all files above some size (which seems to be around 90M...) have that extra blocks (the bigger files have more block). So where do they come from? Used for the management of other blocks? Where can I find the algorithm?

---

### Post by westie457 on 2015-07-05
Maybe this is useful to you. [https://ext4.wiki.kernel.org/index.php/Ext4_Disk_Layout](https://ext4.wiki.kernel.org/index.php/Ext4_Disk_Layout)

---

### Post by ofnuts on 2015-07-05
> **westie457 said:**
> Maybe this is useful to you. [https://ext4.wiki.kernel.org/index.php/Ext4_Disk_Layout](https://ext4.wiki.kernel.org/index.php/Ext4_Disk_Layout)

I asked here because it wasn't really useful (unless I spend a whole afternoon unravelling it).

---

### Post by westie457 on 2015-07-05
Took me all afternoon to read it, still have no idea what it means. Very nearly ended up looking like my avatar.

---

