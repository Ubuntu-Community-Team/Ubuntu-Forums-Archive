---
title: "How to free ubuntu disk space?"
date: 2013-03-12
forum: General Help
---

### Post by karimkhan on 2013-03-12
I have installed ubuntu from windows 7. And I allocated 30GB drive for that. It is showing 6 GB still empty but when I Boot ubuntu, it shows 132 MB space remaining. I doubt that backup file may have consumed space. Currently backup is off. And it shows no previous backup exist. What to do?
its ubuntu 11.04. I have upgraded it from ubuntu 10.04

---

### Post by RoosterHam on 2013-03-13
Is this a physical install? or is it a VM in something like VMWare or VirtualBox? Within the system, is just one root partition and some swap? or are there multiple partitions? Are you saving backups to the same disk? have you got many user files in your /home/username directory?

---

### Post by Impavidus on 2013-03-13
I understand this is a wubi install. Some people make a separate partition, thinking Ubuntu always needs a separate partition or thinking they are doing a regular install, and then install Ubuntu with wubi (the windows installer). If that's the case with you, I think you made a 30GB partition for your wubi install but only made a 24GB virtual partition on it (minus what is used as swap). Ubuntu only sees those 24GB.

---

### Post by Mark Phelps on 2013-03-13
> **karimkhan said:**
> I have installed ubuntu from windows 7. And I allocated 30GB drive for that.

Sounds like a Wubi install.  To confirm that, from inside Win7, look for a file named "root.disk" -- that is the file that Ubuntu treats a Linux filesystem.

Not sure, but I believe that 30GB is the MAX space you can have for a Wubi install -- as it is intended as a way to try out Ubuntu, not to use it for the long haul.

The link below to the Wubi Guide shows how to "migrate" the Wubi installation to a separate partition -- but I should tell you in advance, you need to check the Disk Management Utility in Win7 before you do that, for if you already have the maximum of 4 partitions on the drive, you can't just go off and create a fifth partition as that will change your partitions to Dynamic Disks -- which is something you do NOT want to do.

Wubi Guide:  [https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

---

### Post by karimkhan on 2013-03-13
Yes it is wubi installed,
Thanks all of you for reply!

---

