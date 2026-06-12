---
title: "Restore Clonezilla image"
date: 2014-04-02
forum: General Help
---

### Post by stefano11 on 2014-04-02
Hi all,

I would like to know how to restore the image of 2 disks taken with clonezilla on a new pc (new disk without FS and large enough to contain the partition of old disks). 
I have already tried the restore procedure but I get the error: "Target disk sda does not exist in the image saved fron disk(s) "cciss/c0d0 cciss/c0d1". This image has been saved by more than one disk. The recovery of an image on different disk names is not supported for more than one disc! 'll work just the same as the disc! here we do not create a temporary image! on the other hand, you can try to convert the image with the command cnvt-ocs-dev. "

Has anyone any tips?

Thank you

---

### Post by speartip on 2014-04-02
In my experience with Clonezilla, you have to restore to the same named partition that you cloned from.
For eg. my Ubuntu 12.04.4 system was cloned on partition sda5. So even if I restore it on an a new pc it has to be restored to a partition named sda5 that is at least the size of the original partition.
 You can get round this by entering the cloned -img folder & changing the names of the img.gz folders/files to the partition name you want to restore to.
For example my first Folder is named sda5.ext4-ptcl-img.gz.aa.
If I wanted to restore it to a new PC on say the hda1 partition, I would rename it hda1.ext4-ptcl-img.gz.aa, & do likewise with the other files in the folder.
In my case there are 3 files that are partition specific.
Hope this info is helpful.

---

### Post by stefano11 on 2014-04-03
Hi speartip and thank you for your reply.

You've referred to partitions, I suppose is the same for disks.
I'll try and let you know.


EDIT: I no longer have the chance to fully perform the test. So see you next time. Sorry...

---

### Post by edcompsci on 2014-04-06
I think you just have to make your partitions first. Use the live cd.  I think you have to make the partitions the exact same as you had when you made the image. Not sure if lables matter, but partition size I think so.

---

### Post by sammiev on 2014-04-06
I'm not sure of that error, but I have clone from an image to new drives of the same size or bigger often. Never ran into this well doing so. I had to reinstall the boot-loader for windows and then the grub for linux from time to time.

---

