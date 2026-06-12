---
title: "Yes, Another Partition Question. :D"
date: 2008-05-19
forum: General Help
---

### Post by Exsecrabilus on 2008-05-19
I currently have Ubuntu 8.04 installed on my 70 GB computer. It is using all the space.

I want to try out Linux Mint but want to keep Ubuntu.

So here are my questions:

1. After installing Linux Mint and after editing partitions to fit in Linux Mint, how can I edit partitions if I want to increase space for Hardy or Mint?

2. If I wanted to get rid of Linux Mint, how would I do that? Would I have to decrease the Linux Mint partition to 0% or something?

Thanks for all the help.

---

### Post by muadnu on 2008-05-19
I think you are asking two different things. The first, about resizing partitions. Maybe the easiest way is simply to boot on the Ubuntu Live CD, run Gparted and resize the partitions. This you should be able to do regardless of whether you want to keep just Ubuntu or Ubuntu and Mint. You could also download the Gparted Live CD. The only thing to be careful about is that, depending on what you do, after messing with your partitions the UUIDs of your disks might change, so you would need to change the fstab file (see below).

Now, to install (or uninstall) another distro and dual boot with Ubuntu, check this howto, [http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817), and just be careful when installing grub (I think the best is to install the second distro's grub to its own partition as it is explained in the howto, in which case to remove Mint you would only have to erase the partition and erase the Mint entry from Ubuntu's grub). The howto also explains about changing the fstab file.

Hope it helps...

---

### Post by agim on 2008-05-19
#sudo apt-get install gparted
or install gparted from synaptic.

I browsed your other posts, but didn't see another about partitioning, so I don't know what you know about it, but I use gparted for anything to do with partitions.

It can shrink or grow a partition, as well as creating/deleting.
It would be under System->Administraion->Partition Editor, using the gui.

It is also a part of your Ubuntu livecd, you can find it there using the same method.

---

### Post by Exsecrabilus on 2008-05-19
So Gparted is preinstalled on the Live CD but not on the final install version? O.o

---

### Post by muadnu on 2008-05-19
Yes. In any case, if you want to resize the partition where you installed Ubuntu, you need to do it from the live cd (you need to unmount that partition, which is something you obviously can't do if you are running Ubuntu). I general I always try to run gparted from a live cd, because I've had trouble in the past running it when some partition is mounted (even if it's not the one you are going to use gparted on).

---

### Post by strabes on 2008-05-19
Regarding your 2nd question, to delete linux mint you can just boot the ubuntu live CD again and delete the partition on which it is installed, and then grow the ubuntu one again to take up the full space of the hard drive.

---

