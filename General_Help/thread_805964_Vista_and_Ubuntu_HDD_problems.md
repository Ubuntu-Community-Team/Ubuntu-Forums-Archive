---
title: "Vista and Ubuntu HDD problems"
date: 2008-05-24
forum: General Help
---

### Post by duffyduffman on 2008-05-24
I have a kind of boring problem.
I have way to many partitions.
In my computer I have:
2 S-ATA Westen Digital 160GB
1 S-ATA Seagate Barracuda 160GB
1 ATA Maxtor 300GB
Also connected to my computer by USB 2.0 I have:
1 Lacie BigDisk 500GB
1 Westen Digital 500GB

The Maxtor HDD carries both a Ubuntu and a Vista install.
Now to the problem, I formated one of the WD S-ATA discs in a moving to Ubuntu action. The formating where done in Vista and both before and after it is as all the other disks NTFS.
After the formating I can't mount the disk in ubuntu, works flawless in Vista but does not show up anywhere.
This morning Vista made trash of one of the partitions on the lacie disk so I formated that one to, and now Ubuntu don't find that partition either.

Result:
Disks/partitions formated in Vista does not work in Ubuntu, thay can't even be found.
I have tried both in GPart and fdisk, can't find it anywhere.

Anyone know how I can fix this? It is cool to formate the discs if it is needed. Just that I can't formated in Ubuntu as I can't find the disks and the build in discmanager in Vista seems to make things just worse.

many thanks.
/D

---

### Post by logos34 on 2008-05-24
Can you see any disks from the ubuntu live cd?

Does 

sudo lshw -C disk

show any?

---

### Post by duffyduffman on 2008-05-25
Sudo lshw -C disk
Gives all disks except the missing S-ATA HDD.
So still no sign from it..
I can't se any diffrens between the Lacie disk and the other disks that should effect either.

GPart find the Lacie but say that it is only one partition that takes all the disk not two that it should be.

---

### Post by duffyduffman on 2008-05-27
I have solved one of the problems, the Lacie HDD now all accessable.
I simply had to delete the partition and resize the working partition, in windows.

---

### Post by duffyduffman on 2008-05-28
And now I realized what was the problem with the other hdd..
That hdd is pluged in to a pci card that gives me 2 more S-ATA connections, a few usb and firewire connections, I guess ubuntu does not support that pci card.

And honestly I have no ide what that card might be named, and how I maybe would get it to work.

---

