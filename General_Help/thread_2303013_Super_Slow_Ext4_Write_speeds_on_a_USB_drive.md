---
title: "Super Slow Ext4 Write speeds on a USB drive"
date: 2015-11-15
forum: General Help
---

### Post by andrewcourtemanche968 on 2015-11-15
Hello,
This is my first time on the forum, if im in the wrong place, let me know. Anyway, I am having super slow write speeds on my Ext4 USB flash drive. Its a 64gb Sandisk Cruzer Fit. Im running Ubuntu 14.04. I tried copying 700mb of files to this drive, which was ntfs at the time, and it copied in about 20 seconds. I tried to install a steam library to it, but learned that NTFS drives dont have execute permissions, so, i reformatted the drive to Ext4, and started to copy the 700mb worth of music and pictures back to it, but it didnt look like it was doing anything. I waited, and finally it started to copy. it took around 5 min to copy those files. Then, i started to download a steam game to the drive, and the disk was writing at about 500kb/s. This is dramatically slower than my internet, thats not the problem. What might the issue be? I can give any screenshots, etc, needed to help find a solution. Thanks in advance.
-Andrew

---

### Post by tgalati4 on 2015-11-15
Welcome to the forums.

Open a terminal and look at *iostat*.  That will give you some statistics to work with.

```
man iostat
```

Flash drives are not that [fast]("http://http://superuser.com/questions/317217/whats-the-maximum-typical-speed-possible-with-a-usb2-0-drive").

With typical 15MBytes/sec (or 120Mbits/sec) write speeds, flash drives tend to be the bottleneck.  NTFS took 20 seconds, but did it really write all of the data?  The progress bar is not representative of what is actually happening within the flash drive.  Pull the flash drive right after the progress shows 100% and you will lose data.

---

### Post by andrewcourtemanche968 on 2015-11-15
Yes, I know flash drives aren't that fast, but they also aren't THAT slow. There has to be another problem going on.

---

### Post by mc4man on 2015-11-15
I'd try ext2 to see how it does

---

### Post by tgalati4 on 2015-11-16
Also try a different flash drive from a different manufacturer and smaller size.

---

