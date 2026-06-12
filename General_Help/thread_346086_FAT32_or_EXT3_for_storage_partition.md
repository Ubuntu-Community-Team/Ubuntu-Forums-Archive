---
title: "FAT32 or EXT3 for storage partition?"
date: 2007-01-25
forum: General Help
---

### Post by rko618 on 2007-01-25
I have a second hard drive that I would like to place all of my videos and music on.  This hard drive needs to be readable and writable from both Linux and Windows.  I originally planned to use FAT32 but then I discovered [http://fs-driver.org/](http://fs-driver.org/) which lets Windows read and write EXT partitions.  My question is, which should I use?

These are the pros and cons that I know of

**FAT32 Pros**
[LIST]
[*]Natively readable and writable in windows and linux
[/LIST]

**FAT32 Cons**
[LIST]
[*]Maximum 4GB file size
[/LIST]

**EXT3 Pros**
[LIST]
[*]Does not suffer from fragmentation
[/LIST]

**EXT3 Cons**
[LIST]
[*]Have to use fs-driver under windows which may have problems.
[*]Large overhead? On a 300gb partition 5GB was used after formating.  Nautilus shows even less available (278gb)
[/LIST]


So which would be the better option?  A big consideration for me is I used iTunes to manage my music, will the fs-driver allow iTunes to work properly with my music? By that I mean will it be able to change things like the song information?  Also why does EXT3 use so much overhead compared to FAT?

---

### Post by kalikiana on 2007-01-25
A problem with Ext3 might be windows compatibility where I have personally seen that it depends on the driver you are using, so the best is to test it yourself.
However I strongly recommend Ext3 as in my experience FAT32 on a large drive is extremely unpleasant, speaking of fragmentation and slowness issues. Decide for yourself if the overhead is okay.

---

### Post by Ramses de Norre on 2007-01-25
The ext3 con of the 5gig loss is easily solved: **sudo tune2fs -r 0 /dev/...** (unmount the drive first!)
Don't try this on your root partition though.

---

### Post by Magnes on 2007-01-25
> **Ramses de Norre said:**
> The ext3 con of the 5gig loss is easily solved: **sudo tune2fs -r 0 /dev/...** (unmount the drive first!)
Don't try this on your root partition though.

What does this command do?

---

### Post by kpatz on 2007-01-25
> **Magnes said:**
> What does this command do?It sets the number of reserved blocks in the filesystem to 0.

Reserved blocks are available only to specific users (normally root), so that the system can continue to function if the filesystem gets filled up.

---

### Post by housam on 2007-01-25
I vote for the ext3 , it is more reliable than Fat32 when dealing with big media files.

---

### Post by Ramses de Norre on 2007-01-25
> **Magnes said:**
> What does this command do?

Those reserved blocks are the ones that take up the 5gig you were talking about, with this command you give them free for normal use.

---

### Post by paulg on 2007-01-25
I had to make a similar choice. In the end I went with ext3. My main reasons for this choice were:

[LIST]
[*]fs-driver worked well for me in the past and at the present time when booted into Windows; and
[*]I was planning to spend more time in Linux than Windows and would benefit from the journaling of ext3 while using Linux.
[/LIST]

Hope this helps your decision matrix!

~pAul.

---

### Post by dexter on 2007-01-25
Another pro for ext3 is that it uses journaling. In case of a crash, it will be easier to recover files on an ext3 partition than a fat32 partition.

---

### Post by christooss on 2007-01-25
Please don't use FAT32. Windows XP ****** my usbdisk and all data on it. So far no problems with ext3 just that after formating 160GB disk 2.5GB were already used.

I tried sudo tune2fs -r 0 /dev/... and there is still 2.5 GB of place used

---

