---
title: "NTFS external drive works in Ubuntu NOT WinXP"
date: 2006-12-30
forum: General Help
---

### Post by amwg16 on 2006-12-30
Help please.....:confused: :confused: 
I have a 500gb ntfs external drive that I used in Windows XP before I switched to Ubuntu. I wanted to make use of that drive to interchange files between WinXP and Ubuntu Edgy so I successfully configured NTFS-3g driver to have read/write access in Ubuntu.  Was working flawlessly and then suddenly after a couple days I couldn't access my drive through windows anymore, only ubuntu.

I realize I could just transfer everything to my ubuntu and burn it, but I have over 300gb of info on the external so I wanted to see if i could somehow make windows access it so i can just transfer to that hard drive. 

Note: Windows detects drive and assigns it letter E: but i cannot view any files and when I attempt to read it, it freezes.  Tried running chkdsk w/ multiple parameters, but fails.  Also, I tried a couple ntfs apps and apparently I might have a corrupted partition table.:rolleyes: :rolleyes: Yet.... ubuntu still reads it.  Hhhhmmm?!?!?!?

---

### Post by kwilliam on 2007-01-01
(Disclaimer: I don't have an answer to your question.)

That doesn't sound good.  :(  I guess I won't try to use my dad's 300 GB external NTFS HD for making backups then.  I thought NTFS-3g was supposed to be the best NTFS driver currently, isn't it?

The idea that Ubuntu can read/write on NTFS fine while Windows can't is simply funny, even though it's probably caused by Ubuntu implementing something wrong.

---

### Post by amwg16 on 2007-01-01
Ya I was bummed!!! Love ubuntu but still has some bugs that need to be worked out before I can abandon windows completely.  Till then, as much as it hurts me to say it .... windows keeps me coming back because of it's ease of use and compatibility.  However, it wouldn't hurt to keep checking back on the ntfs-3g development since it is being highly developed.

---

### Post by crispy_420 on 2007-01-01
Do you really need NTFS support?

Do you transfer large files? (larger than 4GB)

If you don't need large file sizes, try fat32.

If you do need large file sizes, try an external drive formatted as ext3. It will flawlessly with ubuntu, no need for beta drivers. And for windows you can get a driver for ext3.

But I would test some files first, you don't want to put some important data on it only to suffer some error and lose it.

---

### Post by cmost on 2007-01-01
You guys, the better solution is to format the drive EXT3 and then use the Ext2IFS.  It provides Windows NT4.0/2000/XP/2003 with full access to Linux Ext2 or Ext3 volumes (read access and write access). This may be useful if you have installed both Windows and Linux as a dual boot environment on your computer.  The "Ext2 Installable File System for Windows" software is freeware.  I've setup my external hard drives with EXT3 and use Windows to read and write flawlessly.  Why trust a reverse engineered driver to read/write NTFS which is so easy to corrupt, even on Windows?  Use an open file system and let Windows read/write that.    I always carry the Ext2IFS driver on my flash drive in case I need to use my portable drives on a computer not equipped with Internet access by which to fetch the driver when needed.  Sticking with NTFS is just furthering your dependence on Windows.  You've made the switch to Linux now ween yourselves off of Windows proprietary disk formats too.  Trust me, it's a far better solution to your problem.

Get the software here (link:)
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by kwilliam on 2007-01-01
@cmost
I'll remember that.  In the mean time, I have no disk space to temporarily store 300MB worth of home video in order to reformat the external drive as ext3.  :)  When I buy an external HD for myself, I plan to do just what you suggest.

---

### Post by crispy_420 on 2007-01-01
Do you have a gmail account?

If so you can use that plugin for firefox called "gmail space". It will turn your unused gmail space into an ftp server. And with no file restrictions (size or type) and will allow up to 1GB of file storage.

> 300MB worth of home video

Did you mean 300GB not MB? If so, hope for a generous friend.  :)

---

### Post by Wim Sturkenboom on 2007-01-02
Not much help, but a HD can always fail in which case you loose all your data on the external HD anyway. So I would start backing up to CD/DVD and next start fixing (FAT32, EXT2/3).

---

### Post by amwg16 on 2007-01-02
Thanks Cmost!!! I really like that idea. Had heard of the ext2ifs, but not from someone that had tried it so now I will definitely be using it. Btw, I managed to get access to my 500gb hd with all my files through windows so now I will save it elsewhere and format to ext3.  One less thing keeping me from completely switching from windows ... now if only the videolinux drivers worked on my logitech fusion webcam, then i would be a happy man!!!! :rolleyes: :rolleyes:

---

### Post by amwg16 on 2007-01-02
Also does anyone know if Gmail space allow you to upload executable files since gmail never allows you to upload them as attachments?

---

### Post by crispy_420 on 2007-01-02
No restrictions on files as far as I know. Worst case scenario, you could always compress them (zip, rar, etc.). I can't be sure since I have yet to try, but give me a bit and you'll have your answer.

Just tried and was able to upload an exe file. So it looks like no restrictions.

---

