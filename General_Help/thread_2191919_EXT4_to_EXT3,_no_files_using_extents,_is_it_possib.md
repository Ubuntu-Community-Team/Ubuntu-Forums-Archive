---
title: "EXT4 to EXT3, no files using extents, is it possible?"
date: 2013-12-05
forum: General Help
---

### Post by blazie151 on 2013-12-05
I have a data only USB HDD I recently switched to EXT4 after verifying on multiple machines it would be read-able. After the conversion, I realized that my router wouldn't mount it. Of course, it was "supported" in the sense that it's supposed to work but the manufacturer can't get their story together. Now, I need to switch back to EXT3, and read that it was possible in the following quote that seems to be all over the internet...

"There is also a downgrade path from ext4 to  ext3, with a method to convert the extent files back to indirect mapping  files. In the case that users prefer to go back to ext3, they can mount  the ext4 file system with the “noextents” mount option, copy the  extent-based ext4 files to new files, rename these over the old extents,  use tunefs to clear the INCOMPAT_EXTENTS flag, and then remount as an  ext3 file system." 
 
Luckily I haven't written any new files to the HDD or migrated the existing files over to extents using chattr. I've checked my file system by mounting  the partition as read-only on another machine and using "lsattr /media/sdd1 -Ra | grep  '^-*e-* '" and found that no files have been written with the extents  flag, so theoretically I should be able to convert this filesystem back  to EXT3 without formatting. Issue is, I cannot find ANY clarification of "use tunefs to clear the INCOMPAT_EXTENTS flag". Does anyone here know where to go from here?

---

### Post by tgalati4 on 2013-12-05
Changing the format of a hard disk is risky for the data contained.  You should have a backup, regardless.  Because both ext3 and ext4 have been around a long time, with lots of minor tweaks between them; it's possible that going from ext3-->ext4-->ext3 may not work correctly.  It's better to get a second drive, with a fresh ext3 format and test it first with your router.  (I presume that you are trying to hook this to a router, because most computers with linux can read ext3 or ext4 without issue).  

*tunefs* is a BSD utility that has been ported to linux.  It is not installed by default:

```
apt-cache policy ufsutils
sudo apt-get install ufsutils
```

"You can tune a file system, but you cannot tune a fish."

Proceed carefully.

---

### Post by blazie151 on 2013-12-05
So there was part of my confusion. I kept thinking it was tune2fs not tunefs. Yes it's being used with a router for network attached storage, and when transferring large files it will be directly connected to a computer for faster speeds. I needed a filesystem read-writable by Windows, Ubuntu, and primarily my wzr-hp-g300nh router running brainslayer v24 21676 (kernel 3.9.4, which is part of why I thought ext4 would be fine).

So just to check here, I know the differences between ext4 and ext3 are greater than extents. From my understanding, I should be able to use tunefs to clear the incompat_extents flag, and be able to remount as ext3. But I'm sure I need to also then clear the uninit_bg and dir_index flags, then e2fsck -pf /dev/sdd1 to repair any issues (which there will be some), before it could be read by my router. My last question is if there will be any known massive data instability clearing the remaining 2 flags.

I appreciate your concern for data safety. I have all of the important stuff backed up, the issue is it's a 1tb drive mostly full, and I'd prefer not to copy that much information back and forth when the filesystem is still compatible and can be converted. Plus it's a learning experience.

Thank you for the help.

---

### Post by blazie151 on 2013-12-05
> **tgalati4 said:**
> Changing the format of a hard disk is risky for the data contained.  You should have a backup, regardless.  Because both ext3 and ext4 have been around a long time, with lots of minor tweaks between them; it's possible that going from ext3-->ext4-->ext3 may not work correctly.  It's better to get a second drive, with a fresh ext3 format and test it first with your router.  (I presume that you are trying to hook this to a router, because most computers with linux can read ext3 or ext4 without issue).  

*tunefs* is a BSD utility that has been ported to linux.  It is not installed by default:

```
apt-cache policy ufsutils
sudo apt-get install ufsutils
```

"You can tune a file system, but you cannot tune a fish."

Proceed carefully.

So I'm confused on the command to remove the INCOMPAT_ENTENTS flag, as tunefs doesn't have it documented that I could find. After installing the package you referred to (which I installed via .deb file as I'm doing this from a Ubuntu Live USB now), I got tunefs.ufs, which does not seem to be able to read the filesystem at all. I simply tried tunefs.ufs -p /dev/sdd1 and got "could not read superblock to fill out disk". Any idea of the actual command I need to clear this flag? Also, is tunefs.ufs what you were referring to or did I just get the wrong deb?

---

### Post by blazie151 on 2013-12-05
Well, after A LOT digging, it looks as if the noextents mount option was removed after Ubuntu 9.04. And the commands in tunefs that allowed it to clear the INCOMPAT_EXTENTS flag in the FS suberblock were talked about but never implemented in final builds, so basically you'd have to find the old patch code and compile the tool to do this yourself. More work than I'm willing to put into this, and not worth the hassle. Basically, deal with the 20+ hours of uselessly transfering data around because the tools to this aren't available at all (ironically because the devs felt it wasn't needed in the final utils because they had too many other options already, lol).

---

### Post by tgalati4 on 2013-12-05
You had me confused as well.  I use *tunefs* for my freenas server which runs ufs and zfs.  *tune2fs* is the tool to use for ext2, ext3, and ext4 tweaking.  I thought they were the same tool.  And you are right, the clear extents option was never implemented.  It's a rare use case to go from ext4 to ext3.  Normally you would be migrating older servers to newer hardware and filesystems.

Hooking up to a router was a good guess though.  ;)

---

