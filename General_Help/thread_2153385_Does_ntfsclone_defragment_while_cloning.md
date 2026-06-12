---
title: "Does ntfsclone defragment while cloning?"
date: 2013-06-10
forum: General Help
---

### Post by amanisdude on 2013-06-10
Okay, I know this may sound like a stupid question since the program works at the "sector level", but I haven't found a clear, straight answer to it yet anywhere, so here it is on these forums:

Does the [FONT=courier new]ntfsclone[/FONT] utility (part of [FONT=courier new]ntfsprogs[/FONT]) defragment the partition being cloned when using the special image format parameter?


**Example Command:**```
sudo ntfsclone --save-image --output sda2backup.ntfsclone /dev/sda2
```


In other words, is there a need to defragment an NTFS volume before backing up with ntfsclone if a defragmented backup is desired? Thanks for any knowledgeable reply.


-[I][B]amanisdude
[/B][/I]________________

---

### Post by psyllex on 2013-06-10
In case you never read this portion:

[B]"ntfsclone will efficiently clone (copy, save, backup, restore) or rescue an NTFS filesystem to a sparse file, image, device (partition) or standard output. It works at disk sector level and copies only the used data. Unused disk space becomes zero (cloning to sparse file), encoded with control codes (saving in special image format), left unchanged (cloning to a disk/partition) or filled with zeros (cloning to standard output)."

I've don't have a lot of experience with it but since you're cloning to /dev/sda2 I would guess that qualifies as a disk/partition and as such is left unchanged.[/B]:guitar::guitar:

---

### Post by ahallubuntu on 2013-06-10
~

---

### Post by amanisdude on 2013-06-16
Hi all,

Sorry it took me a while to report back. I cloned a fragmented file system, and, as I suspected, the file fragmentation on the disk is preserved. [FONT=courier new]ntfsclone[FONT=arial] is truly a sector-by-sector process when working on partition data and doesn't care about the actual files at all, though it does peek at the partition metadata. (Essentially, it operates like [FONT=courier new]dd[FONT=arial] optimized to copy relevant NTFS data only[/FONT][/FONT][/FONT][/FONT]—[FONT=courier new][FONT=arial][FONT=courier new][FONT=arial]I assume it skips the blank space based on the master file table.)[/FONT][/FONT]

Anyway, thanks for the replies, and I hope this helps someone else!


[/FONT][/FONT]–[FONT=courier new][FONT=arial]***amanisdude***
_________________[/FONT][/FONT]

---

