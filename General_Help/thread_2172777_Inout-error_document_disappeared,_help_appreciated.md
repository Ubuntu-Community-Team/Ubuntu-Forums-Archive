---
title: "In/out-error document disappeared, help appreciated"
date: 2013-09-06
forum: General Help
---

### Post by zed2 on 2013-09-06
I had a document in a folder, and when I went to open it, it was nowhere to be found. Initially I thought it was something wrong with the USB where the folder was located, but when I tried to move other documents into the folder it was not possible and a In/out-error came up, saying it was impossible to move files into it, whereas in other folders it was completely fine. I can go into the folder, but it is completely empty. So I started to think that this particular folder might have eaten my document. I also noticed an additional mysterious document I had never seen before outside of the folder, 0 byte and when it is opened this window appears titled ASCII asking whether I want Unicode (UTF), what kind of type setting and what kind of language. I have tried to look for the document any place I could possibly imagine tmp folders, recently opened documents, but I cannot find it. Is there any way to open a larger history of recently opened documents in Libre Office in any kind of way, or is there any other way I could try to possibly recuperate the document? Grateful for some kind of help.

---

### Post by oldos2er on 2013-09-06
Is the file on a flash drive? What file system is it using?

---

### Post by zed2 on 2013-09-06
Yes it was on a flash drive, and the file system is ext3.

---

### Post by oldos2er on 2013-09-06
Have you tried running fsck on it?

---

### Post by zed2 on 2013-09-07
No, I am not sure how to do it. How do you run fsck over the flash drive and specific file? What command should you type and do you need to unmount it?

---

### Post by 3rdalbum on 2013-09-07
Yes, you need to unmount it first.

When unmounted, run:

```
sudo fdisk -l
```

(that's a lowercase L at the end, not an uppercase i)

This will give you a list of connected disks; find the line that corresponds to your flash drive and look at its Device, which will be something like "/dev/sdc1"

Put that device file into this command:

```
sudo fsck /dev/sdc1
```

---

### Post by zed2 on 2013-09-07
I tried it, but it says :
fsck from util-linux 2.19.1
fsck: fsck.ntfs: could not be found
fsck: Error 2 when fsck.ntfs ran for /dev/sda1

---

### Post by zed2 on 2013-09-07
I also tried fsck.vfat, could it work? Which alternative could work?

Output:
usage: fsck.vfat [-aAflrtvVwy] [-d path -d ...] [-u path -u ...]
               device
  -a       automatically repair the file system
  -A       toggle Atari file system format
  -d path  drop that file
  -f       salvage unused chains to files
  -l       list path names
  -n       no-op, check non-interactively without changing
  -p       same as -a, for compat with other *fsck
  -r       interactively repair the file system
  -t       test for bad clusters
  -u path  try to undelete that (non-directory) file
  -v       verbose mode
  -V       perform a verification pass
  -w       write changes to disk immediately
  -y       same as -a, for compat with other *fsck

---

### Post by oldos2er on 2013-09-07
> **zed2 said:**
> I tried it, but it says :
fsck from util-linux 2.19.1
fsck: fsck.ntfs: could not be found
fsck: Error 2 when fsck.ntfs ran for /dev/sda1

I'd be very surprised if your flash drive is /dev/sda. If you run *sudo fdisk -l* then insert your flash drive, give it a few seconds to automount, then rerun *sudo fdisk -l* it should be easy to note the differences.

You could use gparted too. It's not installed by default by you can get it with ```
sudo apt-get update && sudo apt-get install gparted
``` Then with the flash drive inserted run gparted, find the flash drive, make sure it's not mounted, right-click on it to 'Check....'

---

### Post by zed2 on 2013-09-09
So I did the fsck, but it didn't work, I pressed correct, but it still said system unchanged as below:

Start does point to root directory. Deleting dir. 
Reclaimed 6 unused clusters (196608 bytes).
Free cluster summary wrong (392515 vs. really 392521)
1) Correct
2) Don't correct
? 1
Leaving file system unchanged.
/dev/sdb1: 128 files, 102493/495014 clusters

So I am trying gparted now, what do you do after check?

---

### Post by zed2 on 2013-09-09
I did the gparted, and it resulted in erasing the corrupt folder, the 0 byte file remaining outside of it and when I tried the fsck again it said,
fsck from util-linux 2.20.1
dosfsck 3.0.12, 29 Oct 2011, FAT32, LFN
/dev/sdb1: 127 files, 102493/495013 clusters

---

### Post by oldos2er on 2013-09-09
I'm a little confused, you said your flash drive was formatted ext3, but seeing **dosfsck 3.0.12, 29 Oct 2011, FAT32, LFN** and **fsck: fsck.ntfs: could not be found** makes me wonder. With the flash drive inserted can you post the output of ```
sudo fdisk -l
```

---

### Post by zed2 on 2013-09-09
Here it is:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a1247

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   308389887   154193920   83  Linux
/dev/sda2       308391934   312580095     2094081    5  Extended
/dev/sda5       308391936   312580095     2094080   82  Linux swap / Solaris

Disk /dev/sdb: 16.2 GB, 16225665024 bytes
256 heads, 51 sectors/track, 2427 cylinders, total 31690752 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    31690751    15844352    c  W95 FAT32 (LBA)

---

