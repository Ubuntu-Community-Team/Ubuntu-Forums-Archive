---
title: "mounting my c: alongside my external."
date: 2014-01-03
forum: General Help
---

### Post by silvervulpus on 2014-01-03
i have a terabyte internaldrive installed on my system and an external terabyte system also attached, when i partitioned my internal HDD and split it between ubuntu 12.04. (updated today, as i had to install wacom drivers for friends tablet) it mounted, my external drive and my system restore partitions on /media, but it didnt mount c:\, now i visited the forum instructions on [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions) and i followed the instructions, i altered the fstab and everything, however, still no c:\ on boot. an dont want to unmount my external, and yes i want read/write capabilities on ubuntu for my c:\ partition. can someone please help me mount C:\ because the system autoconfigured every other partition except my windows 7 partition. below i will include terminal history for an idea of what i did and how far i went before i decided i should stop and seek help before i break something.

    6  sudo apt-get update
    7  sudo fdisk -lu
    8  sudo blkid
    9  sudo mkdir /media/data
   10  sudo cp /etc/fstab /etc/fstab.orig
   11  gksudo gedit /ect/fstab
   12  gksudo gedit /etc/fstab
   13  sudo mount -a
   14  history
i tried to get the results of each of these commands, but i dont remember the command to bring up the actions and the results i history, im looking it up in "the linux command line" and will post the results i got from each of these commands as soon as i can.

---

### Post by Impavidus on 2014-01-03
I don't really know of a command to bring up actions and results, but most of those commands can't really do anything harmful. At least you made a backup of your old fstab. Maybe you can post your new /etc/fstab here? And the output of **sudo blkid**.

I presume you are not hibernating Windows? Because in that case the C partition cannot be mounted. It could also be filesystem damage. Have Windows run its filesystem checks.

Shared data partitions are safe, but there is some risk in mounting the C partition as RW in Ubuntu. It's quite easy to break Windows that way. Mounting a system restore partition doesn't sound very useful either.

---

### Post by Mark Phelps on 2014-01-04
Have to strongly emphasize what Impavidus mentioned -- mount Windows OS partitions and Windows Recovery partitions using Linux is seriously risking filesystem damage to both.  You should avoid doing this, because if you corrupt either, then (1) you won't be able to boot Windows to repair it, and (2) you won't be able to do a Recovery operation.

---

