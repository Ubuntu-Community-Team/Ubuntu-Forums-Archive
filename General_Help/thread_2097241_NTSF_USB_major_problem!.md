---
title: "NTSF USB major problem!"
date: 2012-12-22
forum: General Help
---

### Post by Zirts on 2012-12-22
Hi,

I have this problem with using USB sticks that have been formatted to NTSF.
Basicly when I start to copy a file onto one of thoes USB sticks, it copys it with the right speed till like 40 or 70% and then it suddnely stops and starts to transer the file at like 1mb/s or not at all which leads to the point where I have to hard-eject the flash drive to get the computer to respond to anything at all. (During that process the computer is in a coma..)

This problem occurs on my computer with which has ubuntu and windows both on it. It does not matter which one I use, the problem will not go away..
Also It is worth mentioning that it occurs on both my laptop and my desktop computer. Does not matter which one I use.  And I have bought like 6 flash drives now and all of them have the same problem on NTSF. 2 of them are 16GB and others are 8 GB.

What can I do to solve this problem?

---

### Post by Cheesehead on 2012-12-22
How big is the file?
How big is the drive?
How much free space is on the drive?

---

### Post by sudodus on 2012-12-22
I think it is because the USB flash drive is so slow. It helps (speedwise) to use a file system without journaling, but then it will be less safe concerning errors.

The standard file system for USB flash drives is FAT32, the ancient system. Unless you have files larger than 4 GB, it is OK. You can also use ext2 (but Windows can't read it).

I try to buy fast USB sticks. They may cost a little more, but it's worth a lot to increase the speed.

The best USB flash drives are the USB 3 ones. Even if you don't have USB 3 on your computer, they will be faster, because the flash memory is faster, and the USB 2 capability will be better utilized.

Another problem with USB drives is that it is very slow when writing many (small) files.

And if you have no patience, and pull the stick before it has finished writing, you are likely to corrupt the file system.

Check in a terminal window with ```
sync
``` which will not return to prompt until the writing has finished

---

### Post by Zirts on 2012-12-22
To both replies:

I am copying over 5GB files on thoes drives. It's mostly just 1 file which is over 5GB so it is not many small files.

There is enought space, i am using NTSF because I need to copy the bigger files.
So my problem still persists.. 
Buying a USB 3.0 does not fix it also, It indeed goes a LOT faster at first BUT like a I sayd at 40% or 70% it stops and goes to about 1mb/s tranfer speed.

This is not a drive space problem, it's something else.

Edit:
And to answer thoes

How big is the file? 5.67 GB
How big is the drive? 8GB 16GB and 32GB
How much free space is on the drive? Fully free, just formatted.

---

### Post by sudodus on 2012-12-22
Try to monitor the read/write activity with
```
sudo iotop -o
``` It's in the repos, simple to install.

Because of the big file(s) you can't use FAT32, so try with the ***ext2*** file system, I think it will be much faster for two reasons:

1. No journaling
2. Native to linux, so better interface than for ntfs

---

### Post by sudodus on 2012-12-22
I just stumbled on this link
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=2074692[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2074692")
Could it be the same problem?
What version of Ubuntu are you running?

---

### Post by Zirts on 2012-12-23
Hey,
ext2 worked, so I am able to use that with my GNU/Linux system atlast :) 
But I still need to look for a solution for windows tough, as I need use one of thoes drives on windows from time to time also.
But thanks !

---

### Post by sudodus on 2012-12-23
You might solve that problem with an ext2 driver for Windows

[[COLOR="Red"]http://sourceforge.net/projects/ext2fsd/[/COLOR]]("http://sourceforge.net/projects/ext2fsd/")

---

### Post by Zirts on 2012-12-23
Thank you! That was exactly what I needed!

---

### Post by sudodus on 2012-12-23
You are welcome

:KS

---

