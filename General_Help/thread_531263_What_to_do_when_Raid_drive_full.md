---
title: "What to do when Raid drive full?"
date: 2007-08-21
forum: General Help
---

### Post by jarmen on 2007-08-21
I have Feisty running a software Raid 1, two 200 gb drives (single 40 gb for os).  I'm currently using it to maintain media files (in a studio).  
The Raid is almost full.  Is it possible to pull a drive, store it and access it later by another computer (Win/Mac?), put a new 200 gb drive in it's place, format the Raid and start again?  
From what I understand now, both 200 gb drives function as one with the data mirrored, so one should be sufficient to store as an archive.  What I don't know is if the data is accessible by another computer if that drive was just pulled and installed into a new computer.

---

### Post by kidders on 2007-08-22
Hi there,

Your post is *very* low on detail, so I'm making a couple of assumptions:
[LIST]
[*]You're using software RAID (since you mentioned plugging parts of your array into other computers).
[*]Your array is not FAT or NTFS (since using either would be daft).[/LIST]If I'm on the right track, then you shouldn't have any problems. It would however be important to be sure that when you reinitialise your RAID array, with the new hard disk in it, the array's UUID is not the same as the original ... to avoid any confusion in the future. Any misunderstandings about which disks belong to what would be disastrous.

Anyhow, when you connect the removed disk to something, it should appear as a clean, degraded array. I seriously doubt that Windows will cooperate, but I imagine MacOS can be *made* to do so (ie a Darwin port of mdadm may well be available), depending on the filesystem you're using.

---

### Post by jarmen on 2007-08-24
Thank you.  I apologize for lack of details...yes, it is software raid and formatted as Linux.  So you don't there is a way to just plug a drive into a Win machine and have it recognize it and the files made available?  Also, why would Fat32 or NTFS be a bad choice?  Aren't those more compatible with Mac/Win?

Thanks

---

### Post by kidders on 2007-08-24
Hey again,

> **jarmen said:**
> yes, it is software raidIn that case, any Linux box will (as I mentioned) be happy to let you access one RAID 1 member. Any OS with a suitable port of mdadm and support for whatever filesystem your array uses will also work fine. Unfortunately, Windows is unlikely to have either. Conversely, if you had used any form of *hardware* RAID, compatibility would quite possibly have been confined to the specific computer that created the array ... so comparatively speaking, you're lucky!

> **jarmen said:**
> why would Fat32 or NTFS be a bad choice?Given the kind of performance Linux's software RAID is capable of, FAT & NTFS just don't cut it. They are exceptionally poorly designed. Even where RAID is *not* involved, it's best to avoid these filesystems where possible, since they don't support the concepts of UID/GID-based file ownership & octal permissions, fundamental to almost every operating system in the world.

I've found HFS to be by far the best choice where Mac compatibility is concerned. When it comes to Windows, whether to choose FAT (which has better cross-platform support) or NTFS (which has fewer ridiculous limitations) often depends on the specific situation.

If you want to be able to reliably access the contents of your archived RAID disk on Windows & Mac platforms, I would suggest copying your data, stripped of any RAID structures, to a HFS filesystem. Doing so will preserve things like symlink structures, file ownership, and so on, that aren't supported by Microsoft operating systems.

Perhaps you could...[LIST]
[*] Intentionally degrade your current RAID1 array, and change its UUID.
[*] Re-attach the removed RAID member, which would now be treated as an entirely new array.
[*] Attach a third disk drive and copy the contents of the now outdated RAID mirror onto it.
[*] Remove the third disk drive.
[*] Force the disk you initially removed from your RAID array back in to it, and verify that it starts to re-sync.[/LIST]That's a hell of a lot more long-winded than "Whip out a disk and put it in a cupboard" ... but if you need hassle-free access to your archived data from multiple operating systems, you may not have much choice. :-(

---

### Post by jarmen on 2007-08-24
Thanks again.  Given that last suggestion, okay do you think this scenario would work?  I pull one of the drives from the array and use a USB drive case to access it?  I would then insert another drive in its place, format the raid and start fresh.

I hope these questions help someone else also down the line.:)

---

### Post by kidders on 2007-08-24
> **jarmen said:**
> do you think this scenario would work?Only if you can live without Windows accessibility, and only have Mac compatibility subject to various provisos ... but yes, it would work.

As I mentioned in my first post though, you would need to verify that the resulting pair of arrays didn't have the same UUID, or disaster would ensue.

---

