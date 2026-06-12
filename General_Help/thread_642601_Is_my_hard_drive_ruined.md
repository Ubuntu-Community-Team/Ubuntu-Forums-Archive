---
title: "Is my hard drive ruined?"
date: 2007-12-16
forum: General Help
---

### Post by mojogil on 2007-12-16
I have a Samsung 160 gig hard drive that I put in an external case.  I had it plugged into the Mac and was formatting it so that I could write to it from all 3 OS's that I have: Mac, Ubuntu, and Windows.
One of the kids either unplugged it or killed the power to the drive before it was done.  Now no matter what I do I can't get any computer to recognize that this drive exists.  I've tried gparted, Acronis, Windows boot, and mac.
Any ideas?
Thanks,
Gil

---

### Post by Pumalite on 2007-12-16
Get a Gparted Live CD and see if it sees it. Then format it.

---

### Post by ~LoKe on 2007-12-16
The LiveCD is probably your best bet.  I can't imagine it being dead because of something like that.

---

### Post by mojogil on 2007-12-16
Ok, I downloaded a gparted live cd and ran it.  It didn't  see the hard drive.  When I plugged the drive into my windows xp machine, it loaded the usb drivers and then discovered the samsung 160 gig drive but when I go to "my computer" it isn't there? Nothing I have seems to be able to see this hard drive?
Any ideas?
Thanks,
Gil

---

### Post by CouchMaster on 2007-12-16
Put the HD into a computer as master and try the good old Win98 boot disk - fdisk and format...

---

### Post by information_entropy on 2007-12-16
> **CouchMaster said:**
> Put the HD into a computer as master and try the good old Win98 boot disk - fdisk and format...

This is good advice.

USB connected drives do not recover from a messed up
format very well, if at all.

Removing the drive from the case, and installing it as a normal drive
will usually allow you to recover or reformat the drive.

Gparted Live CD,  Windows, or Gparted on the Ubuntu Live CD
should do the job.

But you will probably have to remove the drive from the external
USB case

---

### Post by mojogil on 2007-12-17
IT WORKED!
I put the hard drive in my desktop and booted with the GParted Live disc.
It found the drive and I was able to make a partition and format it.
Thanks to all! You helped me save my 160 gig backup drive.
Gil

ps.  I don't know how to mark this thread as "Solved"?

---

### Post by danwood76 on 2007-12-17
thread tools at the top then edit thread I think.

I would never format a hard disk in a USB caddy btw, those things are more unstable than  windows! plus they dont normally write to the MBR of the disks.

---

### Post by mozetti on 2007-12-17
FYI - the reason it didn't show up in "My Computer" is because there was no partition on it. You would have had to go into **Disk Management** in Windows to see if the physical drive showed up. Hard drives without partitions (or functioning partitions/partition table) don't mean anything to a computer.

---

### Post by danwood76 on 2007-12-17
sorry for being pedantic but you mean operating system as opposed to computer.

A blank hard disk can still be used by a computer even without partitions on the disk, its just that the operating system needs the partitioning so it knows the structure of the data on the disk. :) again sorry for the padantic nature of my post

---

### Post by Pumalite on 2007-12-17
> **danwood76 said:**
> sorry for being pedantic but you mean operating system as opposed to computer.

A blank hard disk can still be used by a computer even without partitions on the disk, its just that the operating system needs the partitioning so it knows the structure of the data on the disk. :) again sorry for the padantic nature of my post

The thing that matters is that the guy fixed his drive.

---

### Post by danwood76 on 2007-12-17
Aye tis true!

---

