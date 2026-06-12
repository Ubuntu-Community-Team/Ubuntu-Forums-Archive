---
title: "Windows XP ate my USB disk!"
date: 2007-05-29
forum: General Help
---

### Post by TomiP on 2007-05-29
I have an external 300GB Lacie hard drive with an original FAT32 filesystem that I mostly use for backing up my Windows partition stuff. Since I use Windows pretty rarely these days however the disk has always been used from Ubuntu only, without problems so far. Until now.

Yesterday I brought the disk along while visiting a friend to copy some files of her machine, which is Windows XP. Since the drive is FAT32 I didn't expect any problems with this. When I plugged the drive in however I noticed that Windows didn't see the contents of the drive, which was a bit worrying. It also claimed that the drive was a Maxtor. Since Windows however reported the drive size and free space correctly I figured that it would not cause any harm - or further harm - to try to copy the files I wanted to copy, so I did.

Unfortunately when I came home I saw that the drive is indeed borked. I can see the files I copied from the friend fine, but I can't access anything else. I see some files but the names of those files are just a bunch of random characters and sizes of the files bear no resemblance to the files that were there. I also have 'Recycled' and 'System Volume Information' directories which are new and probably added there by Windows since I don't think they were there previously.

I suppose that the drive may be a hardware casualty and Windows is not to blame, but in any case the drive is not completely dead so I would like to recover some data if possible. Are there any Linux or Windows utilities I could try? Most of the disk was just for backup and losing that is not a problem but there were some files that at the time were only on that disk and I would like to get to those if possible.

---

### Post by mbradlcu on 2007-05-29
I've seen this problem with usb drives that weren't unmounted properly, maybe relevant,, anyway I would try connecting the drive backup to the "hungry" XP machine, see if the files are there and try and unmount the drive cleanly.. (hope this works)

---

