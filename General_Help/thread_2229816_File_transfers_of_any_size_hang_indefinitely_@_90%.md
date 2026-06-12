---
title: "File transfers of any size hang indefinitely @ 90%, every time. Help"
date: 2014-06-15
forum: General Help
---

### Post by theinfomaven on 2014-06-15
Hey,  Using ubuntu live cd to transfer files to another disk.  Upon doing so, any and all large files hang @ 90%.  The hang lasts all day and refuses to allow me to close any windows. System wont respond but mouse moves.    Tiny files copy just fine.  Any ideas?

---

### Post by sudodus on 2014-06-15
Welcome to the Ubuntu Forums :-)

There are many things that can make a difference in this case.

- What size can be copied and what size cannot be copied? Where is the limit?

- What computer is it

Brand name and model
CPU
RAM (size)

- What version and flavour of Ubuntu are you running live?

- What are the source disk and target disk?

- What are the source partition and target partition?

***Connect the target drive and mount it! Please post the output of the following three commands in a terminal window!***

You can copy and paste the text from the terminal window to the editing windows (for a reply). Select Advanced, mark the text and click on the # icon above the editing window to put the text within code tags

```
sudo parted -l  # ... space minus ell
df -h
free -m
```

---

### Post by theinfomaven on 2014-06-15
Hey,    Thank you for replying!  
 Using latest version of ubuntu.
 Source disk is C drive on the computer. 
Target disk is a usb drive. 
Both drives are full partitions.  
NTFS.  
Drives seem to automatically mount.   
I've tried 8gb files and a 55gb directory. 
There is more than enough space on the secondary drive to do the transfer.  
both transfers hang at 90%.  
Hard to ascertain what the limit is. 
Smaller folders/files seem to work fine.   
PC is hp 2x2ghz dual core centrino running XP (Ubuntu live boot cd currently loaded).  

2gb ram Ubuntu 14.04 LTS Latest version and flavor of ubuntu.  
Not sure what those commands do. The drives are mounted fine.

---

### Post by sudodus on 2014-06-15
**parted -l** will show the partitions and file systems

**df -h** will show the mounted partitions and how much is used and free 'disk free'
[B]
free -m[/B] will show how the RAM and swap are used.

-o-

I think you have no swap (virtual memory), and when the RAM gets crowded, the system cannot manage the copying process. There might be problems with zRAM (if it is used in that particular live system)

Standard Ubuntu is rather greedy for memory, and I think you might succeed much better with a lighter desktop environment, that you get with the Ubuntu flavour ***Lubuntu***. It might also be a good idea to create a swap partition in the fastest drive (the internal one I suppose). With 2.5 GB swap I think you should do well. 

So my first tip is to download and burn an image of Lubuntu 14.04 LTS.

If you still have problems, maybe you should

- try with an ***installed system*** in a USB pendrive (install Lubuntu from a CD disk to the pendrive)
- check that the RAM is good (use ***memtest*** at the boot menu) or
- use a command line tool for the copying: ***rsync*** is a very reliable program or
- maybe you can consider ***cloning*** the whole drive with a special tool instead of copying huge files (***Clonezilla*** is a good tool for cloning).

---

