---
title: "resizing partition busy"
date: 2007-09-18
forum: General Help
---

### Post by rjs82vette on 2007-09-18
My SATA II drive has 2 partitions, root and home. I would like to resize the home partition and copy my xp partition (on another IDE drive) to the SATA drive. This way when I dual boot from Linux to windows (games for the kids) I don't lose the speed of the SATA II drive.

The problem I am having is that I cannot resize the home partition. gparted tell me it is busy. I have searched the forums and everything I can find says to use the Gparted live CD.

Well thats what I am using so that solution is out, I have also verified that the partition is not mounted but I still get the busy error.

Any ideas?

---

### Post by Happy_Man on 2007-09-18
Try using the version of Gparted on the Ubuntu LiveCD. That's never given me any problems.... boot up the LiveCD for Ubuntu and go to System --> Administration --> GNOME Partition Manager.

---

### Post by tszanon on 2007-09-18
I second that. The Ubuntu Live CD comes with GParted. It's a case of booting with it and resizing the partition. Remember to backup your files before the process.

---

### Post by rjs82vette on 2007-09-18
I'll try the ubuntu live cd when I get home...

---

