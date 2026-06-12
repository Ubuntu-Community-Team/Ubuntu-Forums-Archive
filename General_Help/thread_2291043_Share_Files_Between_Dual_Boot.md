---
title: "Share Files Between Dual Boot"
date: 2015-08-17
forum: General Help
---

### Post by bigpappajohn1984 on 2015-08-17
I am Dual Booting Windows 10 and Ubuntu.  I have very easily discovered how to access files from my Win 10 machine in my Ubuntu boot, but how can I access files from Ubuntu while booted into Windows 10?

---

### Post by Bucky Ball on 2015-08-17
Windows will not read EXT4 Linux filesystems. If you want to share files between Linux and Win, best to create an NTFS data partition for the purpose.

It is also not a good idea to manipulate files which are directly on the Win OS partition. This can be problematic. Changes made to files on the Win side while booted into Ubuntu can confuse Win.

---

### Post by jay98 on 2015-08-17
There are some third party software tools that let Windows access ext3, ext4 or ReiserFS partitions, but I am not sure if they work with Windows 10 yet.  You could check out DiskInternal or ext2fsd - do some surfing on google.
Probably the easiest way would be to set up a fat32 partition and save your documents, photos, music, etc. there where both operating systems can read and write.  Or if its just pdf's or something simple, save them to a flash drive, or external hard drive.
Good Luck!

---

### Post by bigpappajohn1984 on 2015-08-17
> **Bucky Ball said:**
> It is also not a good idea to manipulate files which are directly on the Win OS partition. This can be problematic. Changes made to files on the Win side while booted into Ubuntu can confuse Win.

I was using Lightworks with some pics/vids I have on the windows partition.  Could that be problematic?

---

### Post by bigpappajohn1984 on 2015-08-17
> **jay98 said:**
> There are some third party software tools that let Windows access ext3, ext4 or ReiserFS partitions, but I am not sure if they work with Windows 10 yet.  You could check out DiskInternal or ext2fsd - do some surfing on google.
Probably the easiest way would be to set up a fat32 partition and save your documents, photos, music, etc. there where both operating systems can read and write.  Or if its just pdf's or something simple, save them to a flash drive, or external hard drive.
Good Luck!

I'll check out DiskInternal -- I have used their partition recovery software before and was very impressed, so I'll def have to check out that.

---

### Post by Bucky Ball on 2015-08-17
Reading EXT* files from Windows? Hmm. Good luck with that. Not sure if there's anything that does that with EXT4, although there are kludges that have a go at other EXT files, with varying success. Better to avoid and do what is known to work and is pretty much rule of thumb. And avoid FAT32 for the /data partition. Old, slow, and has limitations.

---

### Post by darkomano on 2015-08-17
I would agree with [**[COLOR=#C61919][B]Bucky Ball**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=504316") and have a separate (data only) NTFS partition shared between Windows and Linux/Ubuntu.

Writing to Windows boot partition from Linux is a bad idea (Microsoft terminology: boot partition - where Windows is installed, system partition - where Windows boot files are installed).

Maybe "ext2fsd" is reliable for reading files but I would not use it for writing (yet). ext2fsd is evolving and can be used under Windows 7/8/10.

---

