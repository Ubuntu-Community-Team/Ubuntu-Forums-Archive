---
title: "Where my files?"
date: 2007-02-02
forum: General Help
---

### Post by oplekv2 on 2007-02-02
I have an external firewire/USB2 harddrive that I run around with from linux to mac to windows.  It's partitioned as FAT32.

I looked to see if anyone else had this issue, but I didn't find much.

Today, all my files mysteriously disappeared from my drive, but here's the thing.

Both MacOSX and Edgy (home computer) say that 70/250 gigs are being used.  Both actually count up the right number of files/folders when I open the drive's properties when mounted.

Everything says the stuff is there, but at the mount point, there's nothing.  It's like that entire branch of the file tree got severed.

I've ran fsck on the drive, and it fixed some errors (I'll paste):

```

oplek@oplek-desktop:/media/OPLEK$ fsck /dev/sdb1
fsck 1.39 (29-May-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  71:4f/46, 72:50/41, 73:4c/4e, 74:45/54, 75:4b/4f, 76:20/4d, 77:20/00
  , 78:20/00, 79:20/00, 80:20/00, 81:20/00
1) Copy original to backup
2) Copy backup to original
3) No action
? 2
```

It then fixed some file fragments, which I chose to delete (just ridded a few files), and it ended with this:

```
Reclaimed 126380 unused clusters (-153747456 bytes).
Free cluster summary wrong (5079581 vs. really 5205961)
1) Correct
2) Don't correct
? 1
Leaving file system unchanged.
/dev/sdb1: 54482 files, 2423299/7629260 clusters
oplek@oplek-desktop:/media/OPLEK$                  
``` 

Note I'm not a genius with this stuff.  Is there anything I can do to recover the files (which I'd really like to), or is it a lost cause and I should just reformat the stupid thing?

Thanks

---

### Post by znerk on 2007-02-02
Check if there is a trash folder at it..
I deleted some files at my HD one time too, I found it in a trash folder at the HD

---

### Post by oplekv2 on 2007-02-02
> **znerk said:**
> Check if there is a trash folder at it..
I deleted some files at my HD one time too, I found it in a trash folder at the HD

Pardon me whilst I punch myself in the face.

That was it.  Found the stuff at /media/OPLEK/.Trash-1000/files/OPLEK

Thanks!

---

