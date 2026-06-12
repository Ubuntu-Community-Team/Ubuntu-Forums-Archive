---
title: "Dual Boot FAT32 Partition"
date: 2008-03-30
forum: General Help
---

### Post by SlalomMan on 2008-03-30
I've been using Ubuntu for a while, and recently, having configured all of my sound and wireless drivers, have decided to use it as my primary OS. I am going to leave Vista on the laptop still, just in case I have to use a program that fails in wine. I have a Toshiba A205-S4617 Satellite laptop. I ran into a problem when creating the FAT32 partition, in that I already have four primary partitions. Is there anyway that I can make it a "secondary" partition? Or make the linux-swap a 'secondary' partition?

Here is my configuration:

/dev/sda1 - ntfs - 1.46 GiB: This, I think, is a recovery partition from Toshiba
/dev/sda2 - ntfs - 186.43 GiB: Thi is my windows partition.
unallocated - 30GiB: I shrank my windows partition by 30GB to create this space, which I plan on formatting to FAT32.
/dev/sda3 - ext3 - 14.52 GiB: This is my Ubuntu partition.
/dev/sda4 - linux-swap - 486.34 MiB - This is, obviously, my linux swap partition.

Is there anyway I can make one of these a non-primary partition? I'm relatively familiar with linux and the command line, but I have little experience with partitions.

Thanks in advance!

---

### Post by Fixman on 2008-03-30
You *may* have needed a FAT32 pratition to share between windows and Ubuntu a long time ago, but now Ubuntu can write on NTFS without problems, so the FAT32 partition is unnecessary.

---

### Post by SlalomMan on 2008-03-30
Right. I have been writing on NTFS for a while now, I guess I was just thinking of organizing or something. Is there any difference in speeds writing to ext3 than ntfs in ubuntu? If so, I'd rather put my downloads there, but I'm not sure how windows handles ext3. As of now it ignores it, but I've read about a shell extension that allows browsing of ext3 partitions. I haven't tried it out, though, so I don't know how well it works.

---

### Post by mrsteveman1 on 2008-03-30
The windows ext3 drivers work fairly well

Writing to an ntfs volume with ntfs-3g also works very well, its just as fast as the native kernel ext3 driver right now.

---

