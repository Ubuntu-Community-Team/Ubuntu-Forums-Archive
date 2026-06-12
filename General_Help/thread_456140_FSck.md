---
title: "FSck"
date: 2007-05-27
forum: General Help
---

### Post by atlfalcons866 on 2007-05-27
is it safe to run fsck on a partion that is mounted?  or is there a way to run it on the next boot without waiting every 30 boots

---

### Post by Bachstelze on 2007-05-27
No, it is not safe. To schedule a fsck on a given partition at next reboot, create a file called forcefsck on the root of the partition. For example, to schedule a fsck of your root partition :

```
sudo touch /forcefsck
```

---

### Post by moschops on 2008-02-19
Thanks - it was useful to me too.  One of the many things that Ubuntu needs to have in its admin applets!

---

### Post by GregoYatzee on 2008-04-04
I have a partition on a separate drive that I need to repair, can a boot scan of this partition be scheduled?  Device hda works without problems and is where I am working from right now.  hdb is the one I have been unable to access.  When I have it connected directly to the PC, it hangs.  Below is text of an error I received:

end_request: I/O error, dev hdb, sector 74711119
hda: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: status error: error=0x40 { UncorrectableError }, LBAsect=74711119, high=4, low=7602255, sector=108978999
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 108978999
hda: drive not ready for command
EXT3-fs error (device hdb1): ext3_get_inode_loc: unable to read inode block - inode=4669441, block=9338882
NTFS-fs error (device hda5): ntfs_read_inode_mount(): Device read failed.
NTFS-fs error (device hda5): ntfs_read_inode_mount(): Failed. Marking inode as bad.
NTFS-fs error (device hda5): ntfs_fill_super(): Failed to load essential metadata.

---

### Post by niteshifter on 2008-04-04
Hi,
> end_request: I/O error, dev hdb, sector 74711119
hda: status error: status=0x59 { DriveReady SeekComplete DataRequest Error }
hda: status error: error=0x40 { UncorrectableError }, LBAsect=74711119, high=4, low=7602255, sector=108978999
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 108978999
hda: drive not ready for command
EXT3-fs error (device hdb1): ext3_get_inode_loc: unable to read inode block - inode=4669441, block=9338882
NTFS-fs error (device hda5): ntfs_read_inode_mount(): Device read failed.
NTFS-fs error (device hda5): ntfs_read_inode_mount(): Failed. Marking inode as bad.
NTFS-fs error (device hda5): ntfs_fill_super(): Failed to load essential metadata. 

You have problems with both drives. I'd check connections (power and data) and try another ide cable before going further.

---

