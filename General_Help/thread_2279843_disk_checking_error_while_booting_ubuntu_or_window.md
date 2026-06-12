---
title: "disk checking error while booting ubuntu or windows on dual boot pc"
date: 2015-05-26
forum: General Help
---

### Post by thomas52 on 2015-05-26
hi friends , 
i have installed ubuntu 14.04  along side windows 7 ultimate 32 bit on my pc. when ever i start or boot  windows 7 i have seen disk checking errors.i am afraid that i may loose some of my important files will you please suggest what should i do to remove this disk checking stuff and boot my pc normally. is there any danger of losing  and files which are saved on my hard drive.?
thanks.

---

### Post by v3.xx on 2015-05-26
Sounds like your HDD may be going out.  What does the error say?

---

### Post by thomas52 on 2015-05-26
sir it is not actually the error , it just asks for **** checking with a black screen whenever i boot my pc from windows 7

---

### Post by corti-nico on 2015-05-26
> **thomas52 said:**
> sir it is not actually the error , it just asks for **** checking with a black screen whenever i boot my pc from windows 7

Is it happening every time when you boot on Win 7?
Have you ever tried to let it do check or you've always stopped it?

---

### Post by Vladlenin5000 on 2015-05-26
> **corti-nico said:**
> Is it happening every time when you boot on Win 7?
Have you ever tried to let it do check or you've always stopped it?

^^^^
This. And also, are you mounting and writing to the Windows system partition while on Ubuntu? You shouldn't do that. Windows doesn't like and that alone can explain the (Windows) chkdsk running at each boot.

---

### Post by thomas52 on 2015-05-26
okay.thanks . the disk checking does not run everytime only once in 2 weeks . is it a big issue

---

### Post by SeijiSensei on 2015-05-26
Both Windows and Linux will check disks that were not cleanly unmounted during shutdown.  Never turn off the PC before using the OS's shutdown routine first.

If you need to share data between Windows and Linux, I'd create a separate partition on the drive and format it with NTFS.  Mount it as a separate drive letter in Windows, and somewhere under /media in Linux.  That will keep you from having to touch the Windows system partition with Linux.  Alternatively, if you only need to read information in the Windows partition from Linux, add "ro" ("read-only") to the list of mount options in /etc/fstab.

```
UUID=ABCDEFABCDEF1234 /windows        ntfs    defaults,umask=007,gid=46**,ro** 0  0
```

And, no, usually running chkdsk in Windows isn't a big deal if it happens only occasionally, but it's obviously better to avoid having to do so.

---

