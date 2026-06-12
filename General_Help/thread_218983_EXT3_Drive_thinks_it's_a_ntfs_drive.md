---
title: "EXT3 Drive thinks it's a ntfs drive"
date: 2006-07-19
forum: General Help
---

### Post by b3an on 2006-07-19
My system has 2 drives: hda and sda. hda has 2 partitions one a 25gb ntfs partition and the other a ext3 partition and all was working fine this morning.

Grub is installed on sda as is the actual linux and the swap partitions.

My brother tried to get windows working by using the xp install disk and choosing repair then fixboot and fixmbr.

Now the second partition which was a ext3 drive is being listed as a nfts drive by gparted and fdisk, strangly disks manager still saying its a ext3.

Any ideas on how to fix this?

Thanks in adavnce!:KS

---

### Post by b3an on 2006-07-19
Just to add i get the following dmesg when trying to mount:
```


[17181314.972000] VFS: Can't find ext3 filesystem on dev hda2.
[17181348.352000] NTFS-fs warning (device hda1): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17181348.352000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17181348.352000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17181348.352000] NTFS-fs error (device hda1): ntfs_fill_super(): Not an NTFS volume.
[17181402.312000] VFS: Can't find ext3 filesystem on dev hda2.


```

The windows partition (hda1) is also no longer working :(

---

### Post by b3an on 2006-07-19
Just thought I would let people know how I fixed it.

```
sudo fsck /dev/hda2
```

Took awhile to finish but it's working:)

---

### Post by steve.horsley on 2006-07-19
Nice one. It sounded more serious than that.

---

