---
title: "having trouble resizing partitions"
date: 2007-06-02
forum: General Help
---

### Post by bone2006 on 2007-06-02
I had a lot of NTFS and ext3 partitions and I'm trying to move everything into two ext3 partitions, one for root and one for home.   For some reason I deleted a partition that doesn't seem to allow me to resize anything at all except my swap partition.  I'm not sure what I need to do to move that allocation into my home partition.  

Here's what I get when I do a fdisk -l it's a 320gig HD and SDA7 is home and SDA6 is root.  I'd like to bring some of the unused/unallocated space to either one of these partitions.

*****************************************************************
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1       38913   312568641    f  W95 Ext'd (LBA)
/dev/sda5           35720       35853     1076323+  82  Linux swap / Solaris
/dev/sda6           32999       35719    21856401   83  Linux
/dev/sda7               1       32998   265056340+  83  Linux

Partition table entries are not in disk order
*****************************************************************

Thanks in advance

---

### Post by jimbob on 2007-06-02
It's kind of hard to tell from this.  Do you want to get rid of the W95 partition?

Run Gparted and post a screen shot so we can see the order of the partitions.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by merlinus on 2007-06-02
From what I can tell, it seems that you deleted what used to be sda1, which was probably windows.

That had to be a primary partition.

sda2 is an extended partition, in which three logical partitions reside (sda5-7).

So the problem is that I do not believe you can resize the logical ones to fit into the primary.

It may be possible to move /home into it, however.

There is good info at 

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

that might help.

Good luck!

-merlin

---

### Post by bone2006 on 2007-06-02
I have home where I want it already on the separate ext3 partition.    I would like to get rid of everything have two ext3 paritions one or root and one for home, which I already have and then get rid of anything else and have a swap of 1 gig.

I really don't know what the heck this is, but I'll go ahead and post a screen shot of gparted.

---

### Post by bone2006 on 2007-06-02
here's a snapshot

Thanks so much for helping me.

---

### Post by merlinus on 2007-06-02
Here is one idea:

Re-install ubuntu.  Tell it not to format your /home partition, when you get to that screen.

You can then create / and create /swap, and that unallocated space can be used.

I would, however, ask for other opinions first!

aysiu is very knowledgeable....

-merlin

---

### Post by jimbob on 2007-06-03
Looks fairly simple to me if I understand what you want.

Use Gparted (stand-alone CD) and move your swap to the very end of the disk then extend your root partition th the right to use up all the rest of the space.

Download and burn the stand alone Gparted CD - it is a tool that is well worth the effort and you will use often.

Don't forget to adjust your etc/fstab and menu.lst since the UUID's may change.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by bone2006 on 2007-06-03
merlinus:  what you suggested is exactly what your using.   I just recently reinstalled ubuntu and just named the root, named the home and put a checkbox on the root to format it and then clicked next and proceeded with the installation.

jimbob: I've been using the standalone livecd of gparted that I got from their website.  I only used the gparted in ubuntu to take a snapshot to post here.

I really am not sure what you mean by moving the swap to the end of my disk. How do you preform this operation?

---

### Post by jimbob on 2007-06-04
> I really am not sure what you mean by moving the swap to the end of my disk. How do you preform this operation?

Using the GUI in Gparted, select the swap partition, click on move and drag it to the end of the disk.

If that doesn't work, delete the thing and re-create it at the very end of the disk.

Then you can use your cursor to drag the right graphical margin of your root partition all the way to the new start of the new swap partition.

Presto! you're done.   (use the command [COLOR="RoyalBlue"]blkid[/COLOR] to check that the UUID's of your new partitions match those in fstab and menu.lst after these changes)
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

