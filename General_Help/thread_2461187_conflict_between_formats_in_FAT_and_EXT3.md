---
title: "conflict between formats in FAT and EXT3"
date: 2021-04-26
forum: General Help
---

### Post by radimp on 2021-04-26
Hello folks, 

I was wondering to pose this question to all of you. Lately, all my USB pens (3 in total) were not able to mount and be accessed in Ubuntu.
Beforehand, I've formatted my USB pen on FAT format. Every now and then, I used these USB pens to copy and erase files between USB
and my Ubuntu system driven PC (that is formatted on ext3 file system).

For no reason known to me, as time went by, all my 3 USB pens were not able to mount and I could not access my data on it.
I tried to access my USB pens from Ubuntu system PC.
Could it be that there was a conflict between different formats of a file management (ext3 on my PC and FAT on my USB)?
Otherwise, I cannot explain how the hell all my USB pens went from functional to dysfunctional state.

Thank you for any suggestions and advice,
Radim

---

### Post by speartip on 2021-04-26
I did have this problem a few years ago, but more info is needed. What version & flavour of Ubuntu are you using? Why EXT3 and not 4? Do you also use these USB pens on windows machines? etc....
Also have you tried reformatting a USB pen in Ubuntu? Does that work? If not what errors does it throw up?

---

### Post by radimp on 2021-04-26
Hello all, 
For specification purposes:
I'm using Ubuntu 18.04, so I guess there is EXT3 formatting system? Is that right?
All my USB pens with FAT file management were used for Ubuntu systems only.
Thank you all.

---

### Post by speartip on 2021-04-26
It may well have been 18.04 that I experienced similar problems on. 20.04, which is the latest LTS, I have never had an issue with. 18.04 should have been formatted with EXT4, EXT3 is very old now. Also if your pens are unusable at present & you can afford to lose the data on it, try reformatting one & see if it works now. Use the program Disks.

---

### Post by Yellow Pasque on 2021-04-26
Did they all stop being readable at the exact same time? Did you look for clues in dmesg/journalctl? Are they readable on other systems?

> Could it be that there was a conflict between different formats of a file management (ext3 on my PC and FAT on my USB)?

No. That doesn't make any sense. The format of one volume does not affect the other.

---

### Post by TheFu on 2021-04-26
FAT32 doesn't support POSIX permissions.  Linux creates fake POSIX permissions as part of the **mount** process for file systems like FAT32, exFAT, and NTFS which don't support POSIX permissions.

When I say POSIX permissions, I mean both the permissions in red below and the userid/owner ([COLOR="#00FF00"]green[/COLOR]) and the group ([COLOR="#800080"]purple[/COLOR]).

```
[COLOR="#FF0000"]drwxr-x---[/COLOR] 17 [COLOR="#00FF00"]thefu[/COLOR]   [COLOR="#800080"]thefu[/COLOR]   4096 Apr 25 17:22 thefu
```

Understanding these is important for anyone using Linux.

BTW, EXT3 stopped being used by default around 2012, maybe before that.  EXT4 has been normal for all Ubuntu a very long time.

The main things were using FAT32 would matter is that certain filenames and file size limitations exist in FAT32 that don't exist in most other modern file systems.  The only reason someone should be using FAT32 today would be if they have some specific hardware device that only supports it and does not support exFAT or f2fs or NTFS or any of the native Linux file systems.  All of those are better in many technical ways than old FAT32.

If these usb flash drives are only for use between Linux systems, then using f2fs or ext2/3/4 on them would be better.  f2fs is kinder towards flash storage and tries to minimize the number of writes, extending flash storage lifetime.  For exFAT and f2fs and NTFS to be accessed on Linux, we need to load the software which makes that possible.  

To install all of those packages on 20.04:
```
sudo apt install f2fs-tools exfat-utils ntfs-3g
```
some may already be installed. The command won't do any harm.  Now you just need to mount the storage correctly, setting the specific userid as the owner is required for FAT32, exFAT and NTFS.  Usually, these mount options: 
```
uid=1000,gid=1000,fmask=0002,dmask=0002
```
do what we want, but on a system with multiple userids, the uid/gid numbers would be different per-userid.  For native Linux file systems, those options aren't needed/desired.

---

