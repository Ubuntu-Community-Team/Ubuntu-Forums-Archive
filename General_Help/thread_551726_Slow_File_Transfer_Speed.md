---
title: "Slow File Transfer Speed"
date: 2007-09-15
forum: General Help
---

### Post by mandyfester on 2007-09-15
Hello 

Recently whenever I transfer a file in Ubuntu 7.04 gnome the copy paste speed is very slow. A 700 MB file takes just under 7 minutes. This behaviour happens on the local hard drive and with any connected external hard drive.

This is a recent and very annoyinh problem. Any help is much appreciated.

Thanks

Mandy

---

### Post by The_PhAnT0m on 2007-09-15
I'm assuming you have not changed any of your hardware but just to be safe, have you? Is your hard drive nearly full? How much RAM do you have and how big is your swap?

---

### Post by mandyfester on 2007-09-15
Thanks for the reply.

In answer to your first question I have not changed any hardware.

I have about 10 GB free space on my hard disk, 1 GB of RAM and 2 GB of SWAP space.

Thanks

Mandy

---

### Post by The_PhAnT0m on 2007-09-15
Interesting. Have you installed anything recently? Have you done anything that is not something you do on a regular basis on your computer at all?

---

### Post by mandyfester on 2007-09-16
Hello again. No new software. I have tried booting using a previous kernels but no difference.

---

### Post by dcstar on 2007-09-16
> **mandyfester said:**
> Hello again. No new software. I have tried booting using a previous kernels but no difference.

Check hard drive DMA settings (change /dev/hda for you own drive):
```
sudo hparm /dev/hda
```

---

### Post by mandyfester on 2007-09-16
Hello

Here is the  hdparm ouput

 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 7296/255/63, sectors = 61432497, start = 55777743

The slow file transfer speeds also happen when working with files on my external hard drive.  I have 19 GB free disk space on my laptop.

Thanks again

Mandy

---

### Post by atlfalcons866 on 2007-09-16
What file system are you using?

Are you using ext3? I find ext3 very slow with large files >500MB. You should use XFS if you  are using a lot of large files >500MB.

---

### Post by mandyfester on 2007-09-17
Yes I am using ext3. The file transfer speeds were actually fine up to a week ago. Now it is painfully slow, I even get this problem when copying to a fat32 external disk.

---

### Post by mandyfester on 2007-09-24
Hello

Just an update in case someone else ever has a similar problem I can confirm that this behaviour only happened with a specific file. Other files of similar or larger size work just fine.

---

### Post by speedup on 2007-09-24
Hi guyz I was not able to get this command to work. It gave me an error msg: sudo: hparm: command not found.  What do I need to install to make this work?

> **dcstar said:**
> Check hard drive DMA settings (change /dev/hda for you own drive):
```
sudo hparm /dev/hda
```

---

### Post by bbarcelo on 2007-11-25
> **speedup said:**
> Hi guyz I was not able to get this command to work. It gave me an error msg: sudo: hparm: command not found.  What do I need to install to make this work?

The problem is that the original user entered the command incorrectly. It's not "hparm", its "hdparm".

I'm having the same slow file transfer problems transferring 50-100MB files from ext3 (USB) to an NTFS (IDE) drive. My NTFS (USB) drive transfers very quickly, so it's not my USB. Haven't been able to find a solution yet.

---

