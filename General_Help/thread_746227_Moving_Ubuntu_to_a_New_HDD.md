---
title: "Moving Ubuntu to a New HDD"
date: 2008-04-05
forum: General Help
---

### Post by Schiz0 on 2008-04-05
I have Ubuntu 7.10 installed on an old IDE drive. I recently purchased a larger SATA drive and installed that into my system.

I would like to transfer everything from the original IDE drive over to the SATA drive and eventually get rid of the IDE drive. I assume I can use GParted or something to copy the partitions over from the IDE drive to the SATA drive. But I would have to reinstall grub on the SATA drive so that I can boot off it, right?

Any suggestions for doing this would be appreciated.

Thanks,
~Schiz0

---

### Post by lswest on 2008-04-05
i don't think you can physically move the partitions, however, you can format the sata drive, instally Gutsy on it, and then manually restore your settings using a full system backup you create, or to create a liveCD using remastersys (there is a howto [here]("http://lifehacker.com/software/linux-tip/make-an-ubuntu-backup-live-cddvd-with-remastersys-330181.php")) and then install from that onto the new sata drive.

---

### Post by Schiz0 on 2008-04-05
Hmm. Well the only thing I would like to keep is my settings for xchat/firefox/gnome/etc. So I'm assuming that stuff is located in /home/me/*

So would it work to partition and install Gusty on the SATA drive, then mount the IDE drive and just cp the files from the old /home/ into the new /home/ ?

EDIT: and also, Thanks for the quick reply :D

---

### Post by lswest on 2008-04-05
haha, sorry for being slow to respond this time, was having dinner.  Anyways, yeah, you can either tar your home folder, and then untar it , or just copy the contents of the home folder over to the new one (be sure you include hidden files) and then it should work.

---

