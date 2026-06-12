---
title: "Increasing the size of a Partition"
date: 2006-12-13
forum: General Help
---

### Post by happy-and-lost on 2006-12-13
I've *finally* gone Windows free on my laptop :KS 

I used to have a shared fat32 partition where all my music/etc was kept, and due to practical issues with backing up large amounts of data, managed to get it onto an ext3 partition using large amounts of gparted trickery. I'm now left with a hard drive like this (see attatchment).

I want to merge that free space with sda3 (which is /home). How?

Cheers :mrgreen:

EDIT: forgot attachment! ](*,)

---

### Post by taurus on 2006-12-13
I assume you probably forgot about the attachment but boot with the LiveCD and use gparted to see if you can merge the free space to your /home partition!  You do have a separate partition for /home, right?

---

### Post by johnnymac on 2006-12-13
using fdisk (you may be able to do this with gparted) you can move a partition.  Once moved you can merge them.

This might get you started a big...and google has plenty of tutorials

[http://www-128.ibm.com/developerworks/linux/library/l-partplan.html](http://www-128.ibm.com/developerworks/linux/library/l-partplan.html)

MAKE SURE YOU MAKE A BACKUP...

---

### Post by happy-and-lost on 2006-12-13
> **taurus said:**
> I assume you probably forgot about the attachment but boot with the LiveCD and use gparted to see if you can merge the free space to your /home partition!  You do have a separate partition for /home, right?

Tried that. Why can't I just expand the partition backwards into the free space? GParted doesn't let me, and doing something so big with the CLI scares me!

---

### Post by jimbob on 2006-12-13
Since you are only using 12GB out of the 17GB on sda3 use gparted to create an ext3 partition in the unallocated space, then copy sda3 onto it.

If gparted bitches about the size difference, shrink sda3 before you do it.

Once you get it copied, make sure it works and then delete sda3 and expand the new partition into the newly unallocated space.

Don't forget to modify fstab accordingly because the new partition will probably be sda5 or however it turns out.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

