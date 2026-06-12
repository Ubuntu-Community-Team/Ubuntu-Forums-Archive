---
title: "Resize Partitions Procedure - Lubuntu 14.04"
date: 2014-07-09
forum: General Help
---

### Post by mattw1 on 2014-07-09
I have an old Thinkpad that works beautifully with Lubuntu14.04 (for the most part).  It also has the original XP OS on a separate partition. Now that I have become familiar with lubuntu and like it very much,  I would like to resize the partitions so that most of the hard drive space is dedicated to the Lubuntu partition.  I have a bootable flash drive with Partition Wizard and Gparted on it and am familiar with how those programs work, but would like the exact procedure for doing this resize without losing either OS or the swap partition, which I think is a hazard if I don't do it correctly.

Thx.

[B]Matt W
Lubuntu 14.04
IBM Thinkpad t42
Pentium M
1.70 Ghz
768mb RAM
60gb HD[/B]

---

### Post by yancek on 2014-07-09
The most important information someone here would need would be the number of partitions, their location on the drive and their size which you have not posted.  You can do that with the fdisk command and with df -h.

---

### Post by mattw1 on 2014-07-09
I ran that and here is what I got:

tpad42@tpad42:~$ df -H
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda6        19G   11G  7.8G  57% /
none            4.1k     0  4.1k   0% /sys/fs/cgroup
udev            383M  4.1k  383M   1% /dev
tmpfs            79M  1.3M   78M   2% /run
none            5.3M     0  5.3M   0% /run/lock
none            393M     0  393M   0% /run/shm
none            105M   25k  105M   1% /run/user

---

### Post by mattw1 on 2014-07-09
Posted in error.  see next post

---

### Post by mattw1 on 2014-07-09
Attached is a screenshot of the partitions as shown with gparted

---

### Post by yancek on 2014-07-09
You would need to shrink sda1 and I would not shrink it to more than 11GB.  Make sure there is a little wiggle room there.  I think there could be problems booting if you extend the Extended partition to the left and resize the / filesystem partition.  I would create a separate partition for data in the free space created by shrinking xp and mount it under the /mnt directory putting an entry in the /etc/fstab file for it.

---

