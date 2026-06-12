---
title: "[SOLVED] FakeRAID, fsck error"
date: 2008-06-05
forum: General Help
---

### Post by SnappyCrunch on 2008-06-05
I have a fileserver at my house with a 20GB OS drive, and a FakeRAID 1+0 setup on a Promise controller. That is, I set it up with dmraid and not mdadm. It's 4x40GB drives set up in a 1+0 array, so it should show up in a file manager as an 80GB drive. I connect other PCs in the house to folders on the RAID array via Samba, setting up drive  letters on the Windows PCs to match to folders on the RAID.

A power outage has caused folders on the RAID array to become inaccessible. Basically, when I try to list the contents of any folder that was connected when the power went out, I get the following error message:

```
ls: ./public/: Input/output error
```

The raid array mounts fine, and I can view the contents of any folder that didn't have a drive letter on the Windows PCs.

dmraid -r shows the following information:

```
/dev/sda: pdc, "pdc_ghgddeaj-0", stripe, ok, 78124928 sectors, data@ 0
/dev/sdb: pdc, "pdc_ghgddeaj-0", stripe, ok, 78124928 sectors, data@ 0
/dev/sdc: pdc, "pdc_ghgddeaj-1", stripe, ok, 78124928 sectors, data@ 0
/dev/sdd: pdc, "pdc_ghgddeaj-1", stripe, ok, 78124928 sectors, data@ 0
```


I tried to run a fsck on the drive (/dev/mapper/pdc_ghgddeaj), but I get the error message:

```
The filesystem size (according to the superblock) is 19531232 blocks
The physical size of the device is 9765616 blocks
Either the superblock or the partition table is likely to be corrupt!
```


I tried different superblocks, but I always get the same error.

"fdisk -l /dev/mapper/pdc_ghgddeaj" gives the following result:

```
Disk /dev/mapper/pdc_ghgddeaj: 39.9 GB, 39999963136 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/pdc_ghgddeaj doesn't contain a valid partition table
```



What more information can I provide? How can I repair the array?

---

### Post by SnappyCrunch on 2008-06-06
After hours of banging my head against this problem, the solution turned out to be simple. I deactivated the array (dmraid -an) and then reactivated it (dmraid -ay). Bam. All my files are back. A quick fsck later, and the filesystem is clean.

I am quite relieved, but still a bit angry at how simple this was.

---

### Post by cariboo on 2008-06-06
Thanks for letting us know what you did to repair the problem. Remember to mark this thread solved.

Jim

---

### Post by fjgaude on 2008-06-06
I guess we learn that fdisk doesn't read dmraid arrays, eh? Likely nothing does correctly, likely not gparted?

---

