---
title: "Need help to salvage LVM"
date: 2012-11-16
forum: General Help
---

### Post by GuiGuy on 2012-11-16
Hi all,
I have four 1T drives that were mounted as an LVM  on an unknown linux distro. The original hardware and boot HDD are gone. 

gparted etc reports that the 4 drives are healthy, formatted as ext3. Each disk is shown to have an lvm2 partition.  

With the drives connected, Disk Utility reports them as an array, but when I try to access the array with "Disk Utility" I get "not enough components" errors.

vgscan gives me

```
sudo vgscan
  Reading all physical volumes.  This may take a while...
  No volume groups found

```  

Does anyone know of something else else I might try to salvage this  LVM?

Thanks

---

### Post by GuiGuy on 2012-12-08
I'm pleased to say that Windows came to the rescue via [Raise Data Recovery for EXT3/ EXT4]("http://www.ufsexplorer.com/rdr_ext23.php")

It's a pity similar excellent data recovery tools don't exist in the Linux World :(

---

