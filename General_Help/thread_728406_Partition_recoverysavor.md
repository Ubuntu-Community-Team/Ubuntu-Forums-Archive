---
title: "Partition recovery/savor?"
date: 2008-03-18
forum: General Help
---

### Post by teryowen on 2008-03-18
Alright, I was on my ubuntu machine doing some stuff when i decided to format a partition. I used the gnome partition manager to delete an NTFS partition, rebooted no problem.

Then i went on to use fdisk and wrote a new partition table. At which point after the reboot everything went to hell.

So now my entire hard drive has no partition table, any idea how i can recover the data on it? some sort of live cd to recover the partition or restore it back to what it was.

Any ideas on what to do to save the data. 

Thanks in advance.

---

### Post by ryanhaigh on 2008-03-18
This may be useful: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
Im pretty sure its in the repos so you could use the ubuntu livecd, install testdisk and try to recover your partition information.

---

### Post by uberlube on 2008-03-18
Grab PartedMagic from their website and burn it to cd, then boot as a liveCD. This is a great recovery and partitioning tool. While in it, open a terminal and mount the drive that you want to recover from, then you can save your files to another medium. Hope that answers your question.

---

### Post by kriukov on 2008-03-18
I had a similar problem last year:

[http://ubuntuforums.org/showthread.php?t=482415](http://ubuntuforums.org/showthread.php?t=482415)

If the lost partition is not rewritten with new data, it should be quite possible to restore it.

---

### Post by teryowen on 2008-03-18
Wow,  ryanhaigh thank you so much for the testdisk idea, i burned a gparted cd which had testdisk on it so i restored my linux side completely now i just have one NTFS partition that im not able to mount, its telling me to run chkdsk /f on it, ill see how it goes once i try.

Again thank you for the testdisk advice. 

And from now ill be keeping this gparted liveCD near by.

---

### Post by unutbu on 2008-03-18
Do you know what went wrong with fdisk?
If you have any advice on what not to do, it might be very useful to a lot of people.

---

### Post by teryowen on 2008-03-18
I think what i did wrong was that when i tried to reformat my NTFS partition through ubuntu, i used gnome partition manager, and then i also used gparted, and then i used fdisk, and i think in combination this caused problems to the partition table. Overall though it was just probably me doing something wrong with fdisk which led to the parition table being screwed up.

But to be honest not 100% sure what went wrong all i know is that the partition table disappeared. But testdisk did a wondeful job of recovering everything.

Again thanks for the great help.

---

### Post by unutbu on 2008-03-18
I'm not familiar with gnome partition manager. Is that something different than gparted? Googling gnome partition manager seems to point to gparted...

---

### Post by teryowen on 2008-03-18
Yes Gnome partition manager is GParted.

---

