---
title: "can you unformat ext3?"
date: 2007-04-22
forum: General Help
---

### Post by Jeffa on 2007-04-22
Hello all, 

I've managed to make a colossal mistake. I was trying to create a dual boot system on my laptop. During installation, I tried to manually edit the partition table. In the partition table i selected /dev/hda1 which contained the windows installation. I changed the file system to ext3 and hit "forward". Realizing my mistake, I tried to undo the changes to the partition table, but that didn't work. I tried exiting the installation and rebooting, but when the system comes back up I get a "No opperating system installed" message. 

Since I didn't finish the installation, I don't think the partition was reformatted. I think the windows installation is still there, I just can't get to it. I've tried running the windows recovery disc but to no avail. 

Now when i go back into the Ubuntu installation and get to the manually edit partition table, I see:


Device           Type   Mount Point   Size             Used
/dev/hda1     
  /dev/hda1/  ext3   /media/hda1  29397 mb   642 mb 
  free space                                    30674

When i was trying to create the new partition, I made it 30000 MB. Does this mean that the partition listed under /dev/hda1/ is the old windows installation, and that Ubuntu was going to try and install itself on this partition? 

Am I totally screwed?

Thanks for the help.

---

### Post by dcstar on 2007-04-22
> **Jeffa said:**
> Hello all, 

I've managed to make a colossal mistake. I was trying to create a dual boot system on my laptop. During installation, I tried to manually edit the partition table. In the partition table i selected /dev/hda1 which contained the windows installation. I changed the file system to ext3 and hit "forward". Realizing my mistake, I tried to undo the changes to the partition table, but that didn't work. I tried exiting the installation and rebooting, but when the system comes back up I get a "No opperating system installed" message. 

Since I didn't finish the installation, I don't think the partition was reformatted. I think the windows installation is still there, I just can't get to it. I've tried running the windows recovery disc but to no avail. 

Now when i go back into the Ubuntu installation and get to the manually edit partition table, I see:


Device           Type   Mount Point   Size             Used
/dev/hda1     
  /dev/hda1/  ext3   /media/hda1  29397 mb   642 mb 
  free space                                    30674

When i was trying to create the new partition, I made it 30000 MB. Does this mean that the partition listed under /dev/hda1/ is the old windows installation, and that Ubuntu was going to try and install itself on this partition? 

Am I totally screwed?

Thanks for the help.

If you have just changed the partition type - and not written any data over the directory structure area - then you should be able to recover fairly easily.

Boot up a Linux rescue CD (or maybe the Ubuntu Live CD) and run **cfdisk** in a terminal, this should allow you change the particular Partition Type.

Other "fdisk" programs should also work (sfdisk, fdisk), but cfdisk has a nice interface.

---

### Post by az on 2007-04-22
I suggest parted.

Boot the live cd and run

sudo parted /dev/hda

and then use the recue command,  Rescue will look for a partition in the area you tell it to look at.  If it finds one there that is not in the partition table, it will add it to the partition table for you if you want.

Parted is command-line only, but very straightforward and safe.

---

### Post by Jeffa on 2007-04-22
hmm. So if i run the install cd again, the /dev/hda1 is listed as ext3, but if i run cfdisk the hda1 is listed as the primary boot drive and the FS type is listed as "NTFS". rebooting still gives me the "no operating system" error.

---

### Post by hikaricore on 2007-04-22
Did you try the suggested and probably correct option of using cfdisk to change the partition type back to ntfs?

---

