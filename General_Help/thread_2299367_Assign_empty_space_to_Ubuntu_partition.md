---
title: "Assign empty space to Ubuntu partition"
date: 2015-10-17
forum: General Help
---

### Post by enekoalfer on 2015-10-17
Hey!

I used to have a dual boot with Elementary OS Freya and Ubuntu 14.04, but as I only used Ubuntu, I decided to uninstall Elementary. And so I did, but now I have 250GB of empty space there in my HDD, and I am not able to reassign it to the Ubuntu installation. I have tried with a live CD too, but when I try to assign more space to the Ubuntu partition, I can't give it more than what now has.

This is a screenshot of the messy situation my HDD is living:

[ATTACH=CONFIG]265012[/ATTACH]

It is in spanish but you are clever enough to guess that "sin asignar" means unassigned :lolflag:

So I hope someone has a solution for me! I would not like to reinstall Ubuntu just for getting everything in order :(

Thanks in advance!

---

### Post by grahammechanical on 2015-10-17
The way to do it is to use Gparted from a Ubuntu live session and

1) select sda5 the swap partition and select swap off in one of the menus
2) expand sda2 to take up the unallocated space. This will create unallocated space inside sda2
3) expand sda6 into the unallocated space inside sda2

Like me, you have a BIOS partitioning scheme. This means we can have a maximum of 4 Primary partitions and no more. But we can use 1 primary partition as a special primary partition called Extended partition and in the Extended partition we can have as many Logical partitions was we need.

In your case, sda2 is the extended partition and sda6 and sda5 are logical partitions inside the extended partition that is sda2. To work on the disk we need to have the swap partition set to swap off and first work with the extended partition to create space for the logical partitions inside to expand and move.

Regards.

---

### Post by yancek on 2015-10-17
Another option would be to use a Linux Live CD and simply create another partition from the unallocated space at the beginning of the drive, then create a directory as a mount point for it and then an entry in /etc/fstab if you want it available on boot.

 If you use the method suggested above, you would also need to unmount sda6 prior to resizing.

---

### Post by enekoalfer on 2015-10-18
Done! I followed grahammechanical's instructions and everything went perfectly! No boot repair needed ;) :)

For being honest, I was pretty scared of losing all my files although I had a backup of the most important ones :-? But nothing to worry about now!

By the way, I used a GParted live CD instead of the Ubuntu live session.

Thanks grahammechanical and yancek! :D

[ATTACH=CONFIG]265014[/ATTACH]

---

