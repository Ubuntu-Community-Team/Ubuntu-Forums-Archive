---
title: "Using an external hard drive"
date: 2015-09-14
forum: General Help
---

### Post by theon2 on 2015-09-14
I am running Ubuntu MATE 14.04 and i'm really happy with it. But i want to buy an external hard drive and partition it into 2,3, or even 4 different partitions so that i could install and run other Linux distro's on it. Could someone tell me how i might achieve this please.

---

### Post by yancek on 2015-09-14
Before attaching your external drive, run the command:  sudo fdisk -l(Lower Case Letter L in the command) and copy the output to a file and save it.  When you attach the new drive, repeat the command and compare the output so that you know the names/partition of each drive.  Creating partitions on a new drive is pretty simply with correct instructions.  If you still have your Ubuntu install media, you will have the GParted partition manager on it which you can use to create/delete/resize and format partitions.  The link below is to the GParted Manual which has all the information you will need.  If you have specific questions later, post back.

[http://gparted.org/display-doc.php?name=help-manual](http://gparted.org/display-doc.php?name=help-manual)

---

