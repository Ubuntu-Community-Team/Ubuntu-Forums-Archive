---
title: "Questions about Partimage restoring"
date: 2006-09-15
forum: General Help
---

### Post by Grog140 on 2006-09-15
My hard drive is barely working right now but I was able to make an image of my Ubnuntu install and Windows install though.

My questions:

When I restore the partition images to the new hard drive will I run into any trouble with the Grub or anything?

What should I look out for or make sure of when restoring?

And what is the best way to do it? Should install Windows and Ubuntu, then copy over the installs with Partimage? Or should I wipe all paritions and put on the back up copys of every partition on right now?

Help would be great, thanks.

---

### Post by bryanl on 2006-09-15
You will need to re-install Grub. 

Make sure the partitions you define on the new drive are the same size as the imaged partitions

Use fdisk to define the partions, restore the images, install grub, and you should be ready to go.

It's nice to have the restore images on an external USB drive or a second hard drive.

Having a good system rescue bootable CD makes this easy. I am not sure how Dapper fits this role but I do know there are some good ones out there that are designed for this sort of thing and not all that large a download for the ISO image.

---

### Post by Grog140 on 2006-09-15
Alright, to clarify you say I should:

1) Make Grub the way it is now. (I will do this by installing windows, then installing Ubuntu and resizing that partition to the exact size it is now.

2) Use partimage to copy the backupo windows partition to the current one and then doing the same for Ubuntu.

Is that what you are saying? Just want to make %100 sure.

---

