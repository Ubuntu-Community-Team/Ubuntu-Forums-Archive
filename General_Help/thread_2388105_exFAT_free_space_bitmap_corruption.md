---
title: "exFAT free space bitmap corruption"
date: 2018-03-28
forum: General Help
---

### Post by Sami Lehtinen on 2018-03-28
I'm wondering if anyone else is experiencing / suffering from repeated exFAT free space bitmap corruption? 

Volumes are losing disk space, it's marked as being used even, if it's not allocated to files. Afaik, this is due to free space bitmap corruption. Running [FONT=courier new]chkdsk[/FONT] on Windows does fix this issue. But is there any sane work way to deal with this when using Linux? 

In case when the amount of lost disk space gets too ridiculous. Currently I fix the problem by just copying files from volume, formatting the drive / volume again and copying files back.

Does anyone know, if there are any plans to improve [FONT=courier new]fsck.exfat / exfatfsck[/FONT]?

---

### Post by yancek on 2018-03-28
Running chkdsk on windows should fix an exfat system as it is a little used microsoft proprietary format.  I doubt anyone is spending serious time as a Linux developer to repair windows problems nor is it reasonable to expect it.  If you wand to use windows filesystems, then use windows for it.  exfat isn't usedd much and most Linux systems do not even include software to use it in a default installation.

---

### Post by Sami Lehtinen on 2018-04-02
Yes, running chkdsk /f on Windows fixes the free space bitmap and releases the lost disk space. 

Someone asked if this has anything to do with unclean unmount. Probably yes, I never do it intentionally, but what comes to USB and external drives, it's going to happen sooner or later due to different factors. Like hub failing, not enough power on bus, bad connectivity etc. For this reason having working fsck / chkdsk would be awesome. Because without it, it's obvious that some space is going to get lost sooner or later. Yet for small flash drives, the regular format isn't bad approach anyway. Oh yeah, also exFAT sparse file support is broken with the [fuse-exfat]("https://github.com/relan/exfat").

I also formated a few drives to use [UDF 2.01]("https://en.wikipedia.org/wiki/Universal_Disk_Format") using [udftools]("http://www.linuxfromscratch.org/blfs/view/6.3/multimedia/udftools.html") but as I've read, it got it's own problems. Let's see how it turns out.

I'll mark this solved, because there's nothing really "actionable" clearly to fix this issue.

---

### Post by HermanAB on 2018-04-02
The trouble is that FAT, VFAT, exFAT, Ext2 and a few others are 'lossy' file systems.  These file systems do not have journals and do not store any redundant information that can be used to repair problems easily.

If you want to use them, then you should have a UPS and perform clean mount/unmount operations.  If you unceremoniously yank a simple FS from the system without flushing the buffers, then data loss is unavoidable.

---

### Post by Sami Lehtinen on 2018-04-03
@HermanAB

Yeah, I'm very well aware about all that. Yet another question is how long some writes are being "held back" before getting written to disk. Which of course affects that. And I never yank devices without flushing / unmounting. But as I described that can happen unintentionally with USB due to several factors.

I couldn't find any good info about UDF, so I decided to test it out. It seems that there's [no particular reason to use UDF over exFAT with current implementations]("http://www.sami-lehtinen.net/blog/exfat-extended-file-allocation-table-vs-udf-universal-disk-format-file-system-for-flash-drives"). Both get broken and there's no way to fix those on Linux, other than full format. Yet chkdsk for UDF on Windows did seem much more comprehensive than I expected it to be.

NTFS is quite awesome and reliable. Yet it can get also corrupted, but can be very reliably be fixed (with Windows). Also the journal prevents most of corruption anyway. The problem is that it's just extremely slow on flash devices. Especially with devices with poor random write performance.

---

