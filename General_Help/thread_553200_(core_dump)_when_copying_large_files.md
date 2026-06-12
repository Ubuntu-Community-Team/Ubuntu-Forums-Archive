---
title: "(core dump) when copying large files"
date: 2007-09-17
forum: General Help
---

### Post by becatlibra on 2007-09-17
Well at first I tried, in the GUI to copy a large file (a DVD iso) to a shared hdd in my PC ( it's fat32 and the system is dual boot - oh and it feisty and winxp)  anyway, when I ran md5sum they didn't match up.  I tried cutting and pasting in the GUI and the old file was left behind but no ERROR messages popped or or anything.

Then I tried it at the command line.  It says something about a (core dump) and won't copy.  I google'd for around an hour and found a lot of things involving Fedore and this problem (with large files being copied or moved) and they offered fixes (I can remember extactly what but I change a few values in to unlimited using a command line program.)  Anyway, that didn't fix it for Ubuntu.  Anyone else run into this?  I searched here and didn't find much - I guess and this point I am just frustrated.  I setup a dual boot so I can develop in VB and in Linux and set up a large shared drive for music and backups, etc.  My linux partition isn't that large.  Didn't think it would need to be because I have this place to back up all my files. 

But I can't copy a 4.1 gig file.  It says Core Dump.  As I stated the fedora suggestions didn't help.  Someone mentioned it might be a kernel problem.

I don't know but I need to fix it.

Anyone PLEASE?  I'm sure someone else has run into this.

Thanks

Benjamin

---

### Post by FuturePilot on 2007-09-17
I think it might be because the FAT32 file system can only handle files up to 4GB

---

### Post by digen on 2007-09-17
Yup, FAT32 filesystem has a limit of 4GB. FAT16 has a limit of 2GB IIRC.

---

### Post by becatlibra on 2007-09-17
REALLY???  THEN WHAT TO DO?

Is the NTFS read/write capability of linux good enough and reliable enough that there would be not corruption??  I know there are readers for ext2 but I am not sure about ext3 and again I worry about corruption.

Both seemed to play happily with fat32.  I know the INSERT Security Live Distro can read and write to NTFS (using NTFS3G or something like that) but I CAN'T have windows get corrupted.  Most of my clients want Windows programs so I use Visual Studio.  Plus there is no linux support for my USB turn table that I can find (although the software it came with, audacity, is a linux program.) - anyway, all that is beside the point.

I am open to suggestions on what to do? 

I want one big drive that both OS's can share and that neither OS will corrupt.  

It seems NTFS is probably the way to go but, if it's NTFS, how is the ownership handled when a file is created on the windows side?  What are the default permissions in linux once you switch over on those files?  How about defraging since it's NTFS?  How does the linux FS write to these partitions (meaning will it cause heavy defragmentation?)

What do you guys think?

---

### Post by atlfalcons866 on 2007-09-17
i used ext3 and i never experienced corruption from it. It has a journal which helps protect aginst corruption on a powerloss or hard poweroff. I switched to JFS because ext3 was slow for me. EXT3 dosent have a file size limit i think the max file is limited to how much disk space you have left

---

### Post by atlfalcons866 on 2007-09-17
also jfs is not under windows.

---

