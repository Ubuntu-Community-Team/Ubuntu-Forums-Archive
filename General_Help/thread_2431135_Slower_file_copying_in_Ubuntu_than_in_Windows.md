---
title: "Slower file copying in Ubuntu than in Windows"
date: 2019-11-12
forum: General Help
---

### Post by filud on 2019-11-12
Hi,

I'm using Ubuntu 19.10 and have an issue with copying / moving files from system SSD to USB 3 flash and to home server via 1 Gbps home network and the other way (from USB 3 and home server to system SSD).
The maximum speed I reach is 80 - 85 MB/s, sometimes only 60 MB/s.

When I used Windows, speeds were much better, like 120 MB/s for home server and 250 MB/s for USB 3.

I don't know know why is copying of files so slow.

Do you have some clue?

---

### Post by TheFu on 2019-11-12
What file systems are being used on the source and target?  Native Linux file systems usually have kernel drivers.  Non-native file systems, like FAT32, exFAT, NTFS, do not and will always be slower.  Someday, MSFT might provide native, kernel, drivers. Someday.

---

### Post by filud on 2019-11-12
File system on SSD with Ubuntu is Ext4.
File systems on home server and USB 3 flash are both NTFS.

So that would mean different file systems are the cause of slower transfer speeds.

Update: However, I formatted USB 3 flash to Ext4 file system and transfer speed is even lower, like 20 MB/s.

What's the issue?

---

### Post by TheFu on 2019-11-12
I'm confused.
You are using journalled file systems with a USB flash drive?  With flash storage, using a journalled file system would be hard on the write counts before death.  

I'm also confused about the source and target devices, networking protocols, file systems, and storage being used on each part. Can you please clarify each?

[https://www.howtogeek.com/howto/33552/htg-explains-which-linux-file-system-should-you-choose/](https://www.howtogeek.com/howto/33552/htg-explains-which-linux-file-system-should-you-choose/) explains a little about the major file systems and when to use each.
Some file systems specifically for use with flash storage have been created: [https://en.wikipedia.org/wiki/Flash_file_system#Linux_flash_filesystems](https://en.wikipedia.org/wiki/Flash_file_system#Linux_flash_filesystems)  These are more about reducing write counts than performance.

[https://www.phoronix.com/scan.php?page=article&item=linux_f2fs_exfat&num=1](https://www.phoronix.com/scan.php?page=article&item=linux_f2fs_exfat&num=1) comparison between exFAT and F2FS.  F2FS looks really impressive for performance if only Linux systems will need access to the storage. exFAT did beat it in a few tests, but the lack of Unix permissions makes that a non-starter for many people.  A few months ago, MSFT released their exFAT specs for use by F/LOSS projects and said they wouldn't sue over patents.  [https://www.techradar.com/news/microsoft-is-bringing-its-exfat-patents-to-linux-and-open-source](https://www.techradar.com/news/microsoft-is-bringing-its-exfat-patents-to-linux-and-open-source)  That's a game changer for me. I wouldn't touch exFAT previously.

Everyone has different requirements and some people have non-technical requirements.

---

### Post by filud on 2019-11-13
I read the articles in your links and formatted USB 3 flash drive to exFAT file system.
The transfer speed is now much better, from 150 MB/s to 200 MB/s.
So USB 3 flash drive would be solved.

I have also three hard drives on home server (which runs on Windows 10) with NTFS file systems. The ideal option would be to change file systems to exFAT.

Update: I formatted one hard drive on home server to exFAT but the transfer speed is still slow, only around 40 MB/s.
I use Krusader to transfer files between Ubuntu SSD and hard drives on home server (samba on Windows 10).

---

### Post by TheFu on 2019-11-13
Funny how when 2 different people read the same articles, they come up with completely different outcomes.

For flash storage, I'd use F2FS.  Almost always, it is faster than the alternatives AND has Unix permission support. For tiny file systems, smaller than 1GB, without lots of concurrent write transactions, I'd use ext2 for either flash or spinning disks.

Unix permissions are extremely important to me.

For spinning disks, I'd use ext4 because I want journaling in the file system having lived through pre-journaled file system corruption.  Ext4 is a reasonable default.

>  I use Krusader to transfer files between Ubuntu SSD and hard drives on home server (samba on Windows 10). 
isn't clear.  What does "samba on Windows" mean?

---

### Post by filud on 2019-11-13
Samba on Windows 10 means I have set up in the past file sharing on Windows and Ubuntu can see shared folders without any problem.
I don't have installed samba on Ubuntu, file sharing is disabled.
Could samba cause decrease of speed?

I have formatted one empty hard drive from NTFS to exFAT so Windows can see this drive. I am not sure it Windows would see Ext4.

---

### Post by TheFu on 2019-11-13
Sorry, but I cannot help with Win10 or using any Windows as a file server.  I've never done that beyond a trivial file copy once a month.  I won't leave important files on Windows.  
I haven't used KDE in about 18 yrs.  I know that using Gnome will drastically slow file operations unless a manual mount or autofs mount is setup.  Gnome uses gvfs or gio which are both known for poor performance if either is used to connect to networked storage.  It has been an issue for over 5 yrs. [https://gitlab.gnome.org/GNOME/gvfs/issues/292](https://gitlab.gnome.org/GNOME/gvfs/issues/292)   

Searched for KDE and gvfs found: [https://wiki.gnome.org/Projects/KioGioBridge](https://wiki.gnome.org/Projects/KioGioBridge)

There are other people here with Windows file server expertise. Sometimes it takes a few days for them to see posts.

---

### Post by filud on 2019-11-13
OK, thank you for your help.

If I change system on home server from Windows 10 to Ubuntu, would I see higher transfer speeds?

---

### Post by VMC on 2019-11-13
@filud, I've had same issue. Not only that, but whereas Linux, not just Ubuntu, the mouse is jerky at best when copying or moving files. Windows never slows down mouse movement.

---

### Post by HermanAB on 2019-11-13
Hmm, to me, reliability is rather more important than speed.  Therefore I would recommend NTFS for drives with Windows compatibility and Ext4 (or btrfs) for Linux only drives. All these file systems are journaled and highly reliable.

A modern SSD will outlast me, so I use the above file systems on SSDs also.

---

### Post by TheFu on 2019-11-13
I think the OP is using a flash USB thumb drive, not an SSD or spinning HDD for the target on Windows.

Herman, hope you aren't THAT near death.  I've had 2 SSDs fail with less than 2 yrs of use.

---

### Post by filud on 2019-11-13
@VMC: 
Would the article Remove Old Kernels help me?

How did you solve the issue?

---

### Post by VMC on 2019-11-13
> **filud said:**
> @VMC: 
Would the article Remove Old Kernels help me?

How did you solve the issue?
The kernels shouldn't have anything to do with file copying, unless of course an updated driver is included.
I didn't solve it, just use Windows for NTFS file copying, and Linux for everything else.

---

### Post by HermanAB on 2019-11-13
Regarding SSD lifetime: 
I have three laptops with SSDs and they are all about 8 years old (one Lenovo and two Macbooks).  I also cannot remember when last I had a USB schtick or SD card fail.  

At work, we have been using SD cards in helicopters in the desert for about ten years and so far, none have failed.  We are also using many Getac laptops with SSDs in the desert, for more than ten years and none have ever failed.

These widgets have little computers inside that do wear leveling and which will remove bad blocks from service. The modern architectures and processes make them last much longer than in the previous century.

---

