---
title: "No space left on NTFS partition"
date: 2008-06-26
forum: General Help
---

### Post by dbclinton on 2008-06-26
I have a 61 gig ntfs disk partition that's suddenly filled up. I can't think of anything I've done that should have brought me anywhere close to full. Clicking on disk properties, the "Contents" are described as 

25787 items, totalling 48.7 GB,

but the graphic below is all yellow (0 bites free) and I can't save any files to the disk. The partition is WinXP, but I haven't actually logged into Windows for months (I just use the space).
Is there any utility that can easily search for large swap files that haven't been properly closed or something similar? 

Thanks,
David

---

### Post by Trail on 2008-06-26
Maybe you should log into Windows and scandisk it for errors? I would guess the native tools would be better.

---

### Post by VMC on 2008-06-26
Have you tried just mounting that drive and 'ls -l' inside or what does 'du -h' return.
Also did you use the  disk analyzer, "Applications-Accessories-Disk Usage Analyzer"?

---

### Post by Nopposan on 2008-06-26
If it does turn out that the drive is full, might it be that the drive is just full of fragmented files?

I'm a bit of a yahoo in this regard, but if I were in your position I'd try moving the ntfs partition around with gparted; of course, I'd try that AFTER backing up important data to an external drive or media.  Resizing and moving the partition with gparted is supposed to include defragmenting and essentially rejuvenation of your whole partition, afaik.

Nevertheless, I think you should follow the advice already given and find out what's going on with your drive/partition.

Cheers.

---

### Post by drs305 on 2008-06-26
I think trash in these drives now goes to Trash-1000 (UID) or something like that. Do a search to find your trash folders and then open a file manager to inspect the contents and empty it. For other partitions, substitute them for the **/** if you don't want to search your entire drive (including all mount points).

```
sudo find / -type d -iname *Trash*
```

---

### Post by dbclinton on 2008-06-26
These were all terrific ideas and they've got me back on my feet.
> Maybe you should log into Windows and scandisk it for errors? 

That was the first thing I tried (after reading the responses) and found that XP wouldn't even let me in via safe mode and sysresccd found but couldn't fix some file system problems. I couldn't find an old copy of DOS scandisk to try that (should really keep one on hand).

> I'd try moving the ntfs partition around with gparted

I just didn't have the courage for that!

What I did do was force-mount the drive from within Ubuntu (sudo mount -t ntfs-3g /dev/sda1/media/disk -o force) and started deleting random expendable files which has now given me access to the partition. I'm now poking around trying to find out what's happening. 
Could this spell the final end of XP? :)
Thanks!
David

---

### Post by dbclinton on 2008-06-26
> **drs305 said:**
> I think trash in these drives now goes to Trash-1000 (UID) or something like that. Do a search to find your trash folders and then open a file manager to inspect the contents and empty it. For other partitions, substitute them for the **/** if you don't want to search your entire drive (including all mount points).

```
sudo find / -type d -iname *Trash*
```

But you've got your finger on the problem: Disk Analyzer tells me that 

.trash-dbclinton

on the NTFS partition contains 13 GB of data.

Everything should be fine now. Thanks again.

---

