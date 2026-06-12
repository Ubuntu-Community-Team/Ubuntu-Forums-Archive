---
title: "How do I expand root partition (reiserfs)?"
date: 2006-12-09
forum: General Help
---

### Post by Yob on 2006-12-09
Hi,

I tried upgrading my Dapper system but realized my root partition is too small to do this.
Now I want to expand it, but can't figure out how. I've run gparted from an Ubuntu live cd and resizing my /home partition works just fine.
But the new unallocated space ends up in the far right (in the graphical display in Gparted) and I can't make the root partition bigger.

I've been searching through the forum and it seems I have to move around my partitions, which scares my a little.

Is there a way of expanding my root partition without too much hazzle?

I've included a screenshot of what it looks like now below.

Any help would be greatly appreciated...

---

### Post by budgie9 on 2006-12-09
It may perhaps be better for you to re-install and resize your partitions, when you do so.
All free space in Gparted and Partition Magic is to the right. 
If there is a partition in the way of say the Root partition, to the right of it, it has to be deleted first along with any data on it, that will then be added  to the 'free' spare area. I did see somewhere that it is possible to 'move' an active partition in Windows I believe, but I think you will find it too has it's problems. 
In reality back up your partitions and start again, thus you will make sure you give yourself ample room to work with in the future.

---

### Post by Yob on 2006-12-09
Thanks, i'll give the reinstall a go as soon as i figure out a smooth way to backup the data on my /root partition.

I recon i'll set up the new root on a 10GB partition - does that sound reasonable?

---

### Post by der_joachim on 2006-12-10
Hmmm... If you reinstall, you might want to use LVM. LVM stands for Logical Volume Management and one of the things it does is resize a partition when it gets full. [Read the HOWTO]("http://www.tldp.org/HOWTO/LVM-HOWTO/") for more info if you are interested.

---

### Post by Yob on 2006-12-11
Hi,

Thanx for the replys.
I've decided to reinstall my system and redo the partioning.

First i want to back up my data though, so I plugged in a IDE hard drive i had lying around. (I have sata disk plugged in already), but when i reboot i get a BIOS screen saying "Detecting array..." and nothing more happens.

If i plug out the IDE drive all is back to normal.

By the way I already have two disc drives plugged.

Any ideas to how i might fix this?

---

### Post by smoker on 2006-12-11
i have trouble with my motherboard, to enable sata it disables one of the ide channels, try disconnecting your cd/dvd drive and using that channel for your backup drive. if it works, reconnect your cd/dvd once backup is done.

also, if you wanted to avoid a reinstall, you could delete your swap part, then shrink your data partition, and move it so the unused space is next to your root partition, then expand root, and recreate your swap.

---

### Post by Yob on 2006-12-11
Smoker,

Thanks for the tip. Now when I boot my machine the disk shows up, but for some reason i can't interact with it.
I've tried creating a new partition on it, but Gparted just gives me "Error while setting new disk label".

cat /etc/fstab gives me:
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               reiserfs notail          0       1
/dev/sda3       /home           reiserfs defaults        0       2
/dev/sda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

And in GParted it looks like the screenshot attached.

What am i doing wrong?

---

### Post by smoker on 2006-12-11
i'm not sure about this i'm afraid, but i have had trouble running gparted from the live-cd before. if you can download and burn the gparted boot iso from sourceforge.net, try that and see, i've never had a prob using that.

other than that, maybe someone more knowledgable can advise

---

### Post by Yob on 2006-12-12
Thanks, i'll play around with it a bit more and update the thread if i solve it.

---

