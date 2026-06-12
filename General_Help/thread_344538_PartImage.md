---
title: "PartImage"
date: 2007-01-23
forum: General Help
---

### Post by carverj on 2007-01-23
Hi,
    Is it possible to use a fat32 partition on your slave drive as the destination for your image backup?

---

### Post by paparucino on 2007-01-23
> **carverj said:**
> Hi,
    Is it possible to use a fat32 partition on your slave drive as the destination for your image backup?
Yes. I use a USB stick with FAT partition to save relevant data plus another partions in a windows disk to store/save large amount of files

---

### Post by indytim on 2007-01-23
Just be mindful of the FAT32 filesize restrictions if your output is approaching 4G.

IndyTim

---

### Post by carverj on 2007-01-23
> Just be mindful of the FAT32 filesize restrictions if your output is approaching 4G.


What is the restriction for FAT32 again?

---

### Post by logos34 on 2007-01-23
In other words, your backup image (after gzip/compression) can't be larger than 4GB (largest file size supported by fat32).

---

### Post by carverj on 2007-01-31
So this means you can make the fat32 partition as large as you like, but each file within can be no larger than 4G?

---

### Post by dcstar on 2007-01-31
> **carverj said:**
> So this means you can make the fat32 partition as large as you like, but each file within can be no larger than 4G?

Yes.

---

