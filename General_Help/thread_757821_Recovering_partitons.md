---
title: "Recovering partitons"
date: 2008-04-17
forum: General Help
---

### Post by Mark_in_Hollywood on 2008-04-17
I wanted to put /home on it's own partition per the article at Psychocats.

I was having a difficult time and was getting some help online and that fixed some confusion. But in the confusion, once the partition was being "moved left and resized", the lack of any progress bar or other indicator made me think the process had jammed. So I canceled. Now my Gutsy won't start. It gets past Grub, past, Starting Up, the Ubuntu splash loads about 25%, then I see a screen and it says: /dev/sda1 errors . . . and . . . fsck check forced.

fsck runs, and then the screen flashes 

Multiply-claimed blocks in inode [then a number that changes maybe 1000s of times]

and the system halts. Issuing sudo shutdown now fails, but Alt-SysRq REISUB did reboot.

Choosing Recovery Mode ran OK until the fsck started up and then when it was done gave the same message about multiply-claimed blocks and halted.

Anybody got some experience with how to fix this?

---

### Post by bodhi.zazen on 2008-04-17
First thing to do is boot the live, desktop CD and lets look at your partitions with either 

```
sudo fdisk -l
``` or gparted.

---

### Post by Mark_in_Hollywood on 2008-04-17
ubuntu@ubuntu:/home$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38536   309540388+  83  Linux
/dev/sda2           38537       38913     3028252+   5  Extended
/dev/sda5           38537       38913     3028221   82  Linux swap / Solaris

I'm running the LiveCD on my desktop where the problem is.

A few minutes later:

I have testdisk up and running. I see I have to option of loading the "backup" of (what I'm guessing) is partition information that could fix my problem. Anybody got some experience with testdisk and how to run it?

---

### Post by bodhi.zazen on 2008-04-17
hmmm .... the partitions look "OK"

lets check them and then try to mount them.

First make sure they are not mounted, and if they are unmount them first. DO NOT RUN fsck on a mounted partition.

Then :

```
fsck -rfv /dev/sda1
```

If that runs, try to mount the device :

```
sudo mount /dev/sda1 /mnt
```

Then ```
gksu nautilus /mnt
``` and look at the contents.

---

### Post by Mark_in_Hollywood on 2008-04-17
I sudo umount -a

some would not unmount, obviously.

Ran the first command

fsck -rsv /dev/sda1  

I'm not looking at the argument at the moment, so forgive if it's not -rfv or similar.

a moment later, I saw 

first pass

then a longer moment and the screen went crazy with line after line of 

multiply claimed blocks at inode: 1234567890

as fast as the terminal could process the lines flew past. After more than 10 minutes, the terminal stopped scrolling. 

Nothing else was reported from the terminal and I didn't try the other commands in your post, yet.

---

### Post by bodhi.zazen on 2008-04-17
Reboot to hard drive.

If that fails, as I am mot sure about the exact command you entered, I advise :

```
fsck -rfv /dev/sda1
```

From the live CD on an unmounted partition (repeat).

Be warned, data loss may occur.

---

### Post by Mark_in_Hollywood on 2008-04-17
Sorry to belabor the point

As I typed my response as to what the terminal showed, I could not REMEMBER -rfv

so I typed 3 letters. Maybe it should have been XYZ as I meant, by way of example.

I did type the command in the termnal as you gave it, for the "record".

OK, reboot to hard drive got past Grub, Starting up . . . and then the splash screen which shows about 25% complete when the splash goes to

checking root file system

/dev/sda1 contains a file system with errors, check forced

and then it runs quite a long time doing the fsck

---

### Post by bodhi.zazen on 2008-04-17
OK, thanks for the clarification ...

Let it run .... I find it best not to interrupt these things ...

Error message ?

---

### Post by Mark_in_Hollywood on 2008-04-17
Seemingly 1000s of lines of 

multiply-claimed blocks at inode: then a number.

no error message returned at the terminal. Is there a log file to see?

---

### Post by bodhi.zazen on 2008-04-17
OK, you can try to manually recover.

Again boot the live CD. Make sure the partition is not mounted.

Then :

```
fsck /dev/sda1
```

You will be asked to manually repair the problems. Select yes or the default option. It will look like this :

[http://readlist.com/lists/gentoo.org/gentoo-user/14/72366.html](http://readlist.com/lists/gentoo.org/gentoo-user/14/72366.html)

(scroll through that post, your errors / fix will likely be different, but that gives you some idea of what it may take).

---

### Post by Mark_in_Hollywood on 2008-04-25
I have my entire /dev/sda1 "recovered". By allowing GParted to perform it's "test" function, it has found the multiply-claimed blocks in inode: xxxxx and the 320 gig drive is all good.

I had four or five different posts regarding the problem over the course of several weeks. 

Thread Closed -- Ubuntu Success!!!

---

