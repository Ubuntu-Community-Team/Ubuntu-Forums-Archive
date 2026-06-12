---
title: "does ubuntu do anything"
date: 2007-05-24
forum: General Help
---

### Post by atlfalcons866 on 2007-05-24
does ubuntu do anything in the background when the computer has been idle like optimize the file system?

---

### Post by gustavoberman on 2007-05-24
I think there is no way to optimize a file system if it is mounted
Maybe it is running some other programmed task.
look into the crontab

---

### Post by atlfalcons866 on 2007-05-24
well windows xp does something to the disk when idle. i think it is boot defrag

---

### Post by ryanVickers on 2007-05-24
Well, I'm kind OSist :p but xp is completely retarded!  When it sits for some time idle, it swaps stuff in and out, scrambles stuff up in it's pathetic attempt to defrag the disk (which shouldn't be necessary anyways) and it's always making that annoying scratching, grinding noise!  Have you ever hear that in linux, even when the disk is going 100%!?  I thought not :p  God only knows what xp does (seriously, no one knows! they hide everything) but I think you'll find that if ubuntu is doing anything, it's probably indexing files for faster searching (which is something else windows couldn't hope to do properly in it's wildest dreams, but don't get me started on that now too :))

---

### Post by atlfalcons866 on 2007-05-24
actually the grinding sound is the hard drives heads seeking. I hear that in Ubuntu but not as much as i do in xp. My system is peaceful in Ubuntu.

---

### Post by Subban on 2007-05-25
I believe that ext2/3 (probably ReiserFS and others too) don't need or benifit from defragging because its a heap more careful how it saves stuff to the HD in the first place, Windows (fat32/NTFS/Fat16) just slaps it all into the first available sapce, spreads the rest of the file out of the remainder of the drive and then tries to patch it together again later (defrag)... Linux I understand tends to get it right first time when you save the file originally, keeping it all together.

Someone more authorative may comment/clarify.

---

### Post by ryanVickers on 2007-05-25
> actually the grinding sound is the hard drives heads seeking. I hear that in Ubuntu but not as much as i do in xp. My system is peaceful in Ubuntu.
I know, it's the head going around to all the file fragments.  In linux, they're all in one piece, as they should be.
Well, yes, you'll hear it sometimes, but it's way quieter, and chances are, depending on the files, you won't hear it at all.  When I boot up and do certain things, I notice a hum and such, but for most, even at 100% it's absolutely silent.  where as windows, even a tiny thing like opening a jpg will cause a noise for a short instant (I mean right after you've viewed a file in the same folder)!

> I believe that ext2/3 (probably ReiserFS and others too) don't need or benifit from defragging because its a heap more careful how it saves stuff to the HD in the first place, Windows (fat32/NTFS/Fat16) just slaps it all into the first available sapce, spreads the rest of the file out of the remainder of the drive and then tries to patch it together again later (defrag)... Linux I understand tends to get it right first time when you save the file originally, keeping it all together.
Exactly!  No other OS is that stupid.  That's why the disk i quiet in linux.  I've also noticed one other thing.  In windows, the fan tends to be going a lot, and that makes sense, when playing games and all, but in ubuntu, even a huge load (that would likely produce massive heat) doesn't seem to trigger the fan very much, and although I've noticed my video card sitting at about an average of 10 degrees (c) higher, it's not a problem (still half the max recommended)

---

### Post by atlfalcons866 on 2007-05-26
no matter how intellegent a file system is there will always be some fragmentation. this applies to the linux files systems like ext3 and resiser. When drives fill up at like 5% then fragmentation becomes an issue. Windows Files systems alway fragment. i remember on my old 120Gb harddisk i had 100GB of contagious free space. i sent a video from my camcorder and the file itself went into 1000+ fragments. The file was only 548MB  That was on NTFS.

---

### Post by pointone on 2007-05-27
Fragmentation in ext3 is negligible. Fragmentation is almost non-existent in ReiserFS.

---

