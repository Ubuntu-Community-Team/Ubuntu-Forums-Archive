---
title: "Can't get data from exernal hard drive"
date: 2012-12-08
forum: General Help
---

### Post by user2010 on 2012-12-08
Some time ago I did something wrong trying to make a bootable USB using my external hard drive.  It had to be formatted, but I didn't  proceed the operation (when I got, what was going to happen). Now I still have the data on the hard drive -- when I go to Properties, I see 440Gb used and 60 Gb free space -- but I can't reach it. 

Could you tell me please, is there any way I can do it?

Here is the Screenshot: [http://tinypic.com/r/34ewbv5/6](http://tinypic.com/r/34ewbv5/6)
[IMG]http://tinypic.com/r/34ewbv5/6[/IMG]

---

### Post by TheFu on 2012-12-08
Can't see that image file. Sorry.

I always start with looking at the log files. In this case it is dmesg and syslog. Are there any related errors? If the HDD is recognized, then you just need to look at the partitions. Use **sudo parted -l** for that information.  From there, you need to note the file system type and try to mount it.  **man mount** will explain how to do that.

Of course, it could be that the partitions are already mounted, just not in a place that you are used to seeing them.  Check for this with **df.** That will show all the mounts on a system.

These are all terminal commands. Copy/paste the results here if you need help interpreting. Please DO NOT copy/paste the entire dmesg or syslog output, just the relevant parts - probably 5 lines or less.

---

### Post by 2F4U on 2012-12-08
Looks as if something is wrong since the filenames look strange (unless that is a language I don't know). You can try to rescue the data:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by user2010 on 2012-12-08
> **TheFu said:**
> 
These are all terminal commands. Copy/paste the results here if you need help interpreting. Please DO NOT copy/paste the entire dmesg or syslog output, just the relevant parts - probably 5 lines or less.

Maybe, you have to wait a little bit to see the image.. It's there. 

Here is what I get: [http://postimage.org/image/69u2t9l2n/](http://postimage.org/image/69u2t9l2n/)

Could you tell me please what should I do next?

---

### Post by user2010 on 2012-12-08
> **2F4U said:**
> Looks as if something is wrong since the filenames look strange (unless that is a language I don't know). You can try to rescue the data:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

I tried to do it with GNU Parted. I don't know what I should type in after rescue - in which format should be START and END. Must it be "0  500GB" ?

---

### Post by TheFu on 2012-12-08
> **user2010 said:**
> Maybe, you have to wait a little bit to see the image.. It's there. 

Here is what I get: [http://postimage.org/image/69u2t9l2n/](http://postimage.org/image/69u2t9l2n/)

Could you tell me please what should I do next?

* Please post text, not images in the future. Let's save some storage bits.
*  That information says only sda3 is a Linux-compatible partition. All  the others are either FATxx or NTFS. You cannot boot Linux from those file systems.
* You didn't ask this, but USB2 is extremely slow for running any OS.

To me it appears that everything is fine and you just need to **mount **the specific partitions that you'd like to access. For temporary use, that can be accomplished using the **sudo mount** command.  To learn how read the man page by typing - **man mount**.

You'll probably end up with something like:
```
$ mkdir /mnt/usb
$ sudo mount -t vfat /dev/sdb1 /mnt/usb  
```
OR
```
 $ sudo mount -t ntfs /dev/sda1 /mnt/win_c  
```

I didn't check your exact partition names since they aren't easily seen on this screen.  In the man page for mount, it specifies the different file system types that are supported.  For NTFS, you may need to be careful about the character set (UTF8) and user/group settings too. I dunno since every system is a little different.

Mount requires a directory already exist to mount things onto. There are many subtle options for mount, so it is best to read the man page so you get all that are necessary to your particular setup and understand the good and bad for each.

---

