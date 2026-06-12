---
title: "Wipe OS from 1 partition"
date: 2008-04-30
forum: General Help
---

### Post by pearjam on 2008-04-30
Hi!

I have 7.10 on one partition, and 8.04 on the other. I need to remove the 7.10 to put an rpm version of Linux (or FreeBSD) in it's place for a program called Plesk (for my work) which doesn't seem to get along with 7.10 and isn't supported w/ 8.04 yet.

How do you remove an OS from one partition only? I don't want to even chance loosing the 8.04.

Thanks in advance!
PearJam

---

### Post by tamoneya on 2008-04-30
just go into gparted and delete the partition.  It is very safe since it is a partition and nothing from 8.04 will be if 7.10 if your system is setup how you say it is.  Then when you pop in the RPm distro/FreeBSD you can just tell it to make a partition in the empty space.

---

### Post by SlalomMan on 2008-04-30
Just run "sudo gparted" from your terminal...or better yet boot from a LiveCD first and run the "Gnome Partition Editor." Then simply delete the partition that has the other OS on it...but make sure that you delete the right one! (I would do something like boot to 7.10 and make a file on the desktop called delete.txt so that when you boot from the CD you can look at the disks and see which one has that file on the desktop)

---

