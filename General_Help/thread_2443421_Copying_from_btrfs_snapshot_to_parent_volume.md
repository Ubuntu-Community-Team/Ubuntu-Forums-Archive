---
title: "Copying from btrfs snapshot to parent volume"
date: 2020-05-15
forum: General Help
---

### Post by jlparsons on 2020-05-15
Hi folks, I have a disc with relatively unimportant media which I've converted from ext2 to btrfs.  The conversion has left the existing data on the drive saved as a 'snapshot' called ext2_saved.  I now want to copy the files from this snapshot into the new btrfs filesystem, but despite extensive googling I can't find a way to do this.  It seems the only way to do it is to roll back the conversion, this can't be right?  What I need is a way to mount the snapshot and move the data over to the new btrfs volume.

```
$ sudo btrfs subvolume show /mountpoint
/
    Name:             <FS_TREE>
    UUID:             -
    Parent UUID:         -
    Received UUID:         -
    Creation time:         -
    Subvolume ID:         5
    Generation:         9
    Gen at creation:     0
    Parent ID:         0
    Top level ID:         0
    Flags:             -
    Snapshot(s):
                ext2_saved



```

---

### Post by jlparsons on 2020-05-18
Update - I've tried mounting the file "image" within the [COLOR=#000000][FONT=&amp]ext2_saved folder using mount loop but no joy (error: "[/FONT][/COLOR]can't read superblock on /dev/loop5")[COLOR=#000000][FONT=&amp].  I'm going to try dd'ing it to a blank hdd.[/FONT][/COLOR]

---

### Post by jlparsons on 2020-05-18
Further update - still not sure what happened, but it seems the convert process did not like MBR  I reversed the conversion then converted to GPT and ran an fsck -y on the partition.  All was then hunky dunky.

---

