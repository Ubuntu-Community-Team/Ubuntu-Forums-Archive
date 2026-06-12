---
title: "Grub Error. Please Help!!"
date: 2007-06-16
forum: General Help
---

### Post by bomb-24 on 2007-06-16
Re: Grub error 5 with new drive
I recently installed ubuntu on a flash drive. I didnt want to disturb my xp installation at all. I used a 4 gig flash drive, went through the installation process and when it rebooted and went to the grub menu it stated: grub loading stage 1.5
grub loading, please wait...
ERROR 5
What can I do?? I am out of options. I cant boot my xp now, all I have is the live cd to run. Can someone please help me?

---

### Post by Reugen on 2007-06-16
well according to [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#5_](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#5_) 

"Quoted from the Gnu/GRUB manual5 : Partition table invalid or corrupt
This error is returned if the sanity checks on the integrity of the partition table fail."
and suggest 
"Check the partition table by running fdisk as root ('sudo fdisk -lu) in Linux, or use your favorite partition editing software to make sure one of your partitions has been marked 'active'. 
If no partition is marked as active, you can use Super Grub Disk to do that for you.
If more than one partition has already been marked as active, you need to remove the 'active' flag from one of them, as only one is supposed to be set as active at a time. Use your partitioning software of that."
I would recommend you reinstall grub
[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

also:
does grub come up when the flash drive is not attached? When you intalled did you tell the installe to write grub on the flash disk instead of the mbr? It sounds like grub was written to the mbr on your system, only grub is to big to fit into the mbr, so the majority of it is stored in the /boot folder on your linux installation, which if the portion of grub doesn't have access to teh rest of it it will give an error after stage 1.5(why error 5 i don't know)  to be able to boot back into xp use supergrub (without the flash drive connected, i'm assuming your not going to have the flash drive plugged in all the time) it will write a new bootloader which should allow you to use your xp installation. Now for fixing the botloader on your ubuntu you may want to disconnect the harddrive just to make sure you don't have the same problem again, i think supergrub will work with a flash drive, but i'm not totally sure.

---

