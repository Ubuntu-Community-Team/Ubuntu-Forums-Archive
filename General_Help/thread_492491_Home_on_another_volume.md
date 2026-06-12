---
title: "Home on another volume?"
date: 2007-07-04
forum: General Help
---

### Post by Virgofenix on 2007-07-04
Hi.

A relatively new guy on ubuntu. Still playing with my first install, though its already about 2 months old - so I have to say that I'm already acquainted with how some things work.

I installed Ubuntu on a volume in a brand new 250 GB harddrive. I currently have a 7 GB XP partition, a 27GB data partition, another 192GB data partition, a 1 GB swap, and a 40 GB Ubuntu(Feisty) partition. 

Now, the problem: I don't know if it was possible to select /home's partition during installation. Currently, /home is at the same volume as Ubuntu. I'm planning to reformat all my OS partitions into:

20GB Ubuntu partition(ext3), 19GB XP partition(NTFS), 1GB swap, 250 GB data partition(NTFS)

Can I have /home use the 250GB partition? I want my data partition to be readable from both XP and Ubuntu.

---

### Post by raja on 2007-07-04
You can have /home on another partition and you can choose this during the install, to answer your first question.
To share data with windows, you have to use drivers in windows to read ext2 or use drivers in linux (ntfs-3g) to read from NTFS. Though you can keep your data in the /home partition and share it, I prefer to set up a separate partition for data that is shared with windows and format it as NTFS.

---

### Post by Virgofenix on 2007-07-05
Thanks a lot raja.

Onto another related question: When will the Trash applet on gnome support ntfs partitions?

---

