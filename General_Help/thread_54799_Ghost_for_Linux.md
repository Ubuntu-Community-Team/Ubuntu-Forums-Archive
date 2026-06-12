---
title: "Ghost for Linux"
date: 2005-08-06
forum: General Help
---

### Post by Matchless on 2005-08-06
Hi,
   I have just downloaded the g4l "Ghost for Linux" ISO. I think this is a must have for every linux user. I then did the following:
1.	Download “Ghost for linux” called g4l Get the ISO file and burn to a CD, use it to boot your PC and run ./g4l to enter the prog and use RAW copy to clone the hdd to another hdd exactly. [http://freshmeat.net/projects/g4l/?branch_id=48238&release_id=152670](http://freshmeat.net/projects/g4l/?branch_id=48238&release_id=152670)
2.	Go to your PC with the perfect installation and configuration, add another (destination) drive as ‘slave’ to the ’source’ hdd in the PC.
3.	Now boot the PC from the g4l CD and follow the screen to copy the complete disk to another, hda to hdb, the disk must be the same size or bigger and obviously the destination PC must have the same hardware unless you are going to try and reconfigure afterwards. It takes long, between 1 and 2 hours, but requires no user intervention once started and could be easier than installing independantly on a couple of PC’s at a time, especially if the configuartion of modems and printers are complex and is already done on one PC
4.	This is basically the same as the dd command. The g4l also uses partimage where you can backup files and filesystems. Some users are using Knoppix which has partimage and is bootable, this allows them to also boot from g4l

I would like to know if anyone knows of an easy way to actually make a backup of the partions on the HDD and then write it to the above bootdisk. This then should allow you to backup a 'perfect' installation and the boot another PC or your same PC and write the backed up partitions to the new PC from the CD.
I am sure this is possible.
Thanks
Matchless

---

