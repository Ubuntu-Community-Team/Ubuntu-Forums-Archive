---
title: "Filesystem for USB memory stick?"
date: 2007-07-12
forum: General Help
---

### Post by Afoot on 2007-07-12
Hi,
I just got a new USB memory stick (4GB :)), and it's probably got FAT as its filesystem. Now I was wondering, which filesystem is best to have on it? I don't care about using it in Windows, so maybe ext2 would be a good choice?

Thanks.

---

### Post by netyire on 2007-07-12
Ext3 is great! But the overhead may be high and it may not work on Windows. Since most people in the world today are using some version or form of Windows, use FAT or FAT32 if you want to sustain compatibility issues. Stay away from NTFS like its the plaque :D

If its all linux boxes you're gonna be using, use Ext3. Just make sure you don't pull it out and get everything corrupted. Should you use Ext3, repair is fsck -p /dev/sdb away :D (or whatever the thing happens to be)

Do inform us of your decision.

---

### Post by LaRoza on 2007-07-12
FAT32 Seems to be the best for a flash drive.

---

### Post by Afoot on 2007-07-12
Just checked out some benchmarks ([http://m.domaindlx.com/LinuxHelp/resources/fs-benchmarks.htm](http://m.domaindlx.com/LinuxHelp/resources/fs-benchmarks.htm)). Ext2 is much faster than FAT32, and I don't really see the point in using a filesystem that has to replay its journal every time I mount the thing, like ext3. So I'll use ext2 I think. ;) Thanks for the help.

---

### Post by LaRoza on 2007-07-12
> **Afoot said:**
> Just checked out some benchmarks ([http://m.domaindlx.com/LinuxHelp/resources/fs-benchmarks.htm](http://m.domaindlx.com/LinuxHelp/resources/fs-benchmarks.htm)). Ext2 is much faster than FAT32, and I don't really see the point in using a filesystem that has to replay its journal every time I mount the thing, like ext3. So I'll use ext2 I think. ;) Thanks for the help.

If you only intend to use this flash drive on Linux, EXT2 is much better. FAT32 is just the safest for all around compatibility.

---

### Post by Afoot on 2007-07-12
> **LaRoza said:**
> If you only intend to use this flash drive on Linux, EXT2 is much better. FAT32 is just the safest for all around compatibility.
Yeah, as I said, I won't be using it on Windows. :)

---

### Post by LaRoza on 2007-07-12
> **Afoot said:**
> Yeah, as I said, I won't be using it on Windows. :)

I envy you...

---

### Post by Afoot on 2007-07-12
> **LaRoza said:**
> I envy you...
Things can only get better with Linux so hopefully you won't be envying me anymore soon (or at least in a year or two). :p

---

### Post by LaRoza on 2007-07-12
> **Afoot said:**
> Things can only get better with Linux so hopefully you won't be envying me anymore soon (or at least in a year or two). :p

No, at home I use Linux, but I am at school A LOT. I use portableapps from portableapps.com, so I have OO, FF, Opera, and 50 other programs, but the school uses XP.

---

