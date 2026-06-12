---
title: "Dual boot with windows 10, booting into Ubuntu after windows gives error"
date: 2021-09-05
forum: General Help
---

### Post by zach87 on 2021-09-05
I already ran boot-repair and have the link it said to save, I really need to fix this to be able to do a project for school. Please help I am lost.
[https://paste.ubuntu.com/p/7s7t55xp5n/](https://paste.ubuntu.com/p/7s7t55xp5n/)

---

### Post by oldfred on 2021-09-05
Please do not post duplicates, we all are volunteers and need to know what others have posted.

---

### Post by oldfred on 2021-09-05
First boot Windows & run chkdsk and make sure fast start up is off.
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Then boot file installer & run fsck on /dev/nvme0n1p5.
To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required, Run both commands as they have different parameters.
sudo e2fsck -C0 -p -f -v /dev/nvme0n1p5
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/nvme0n1p5

Your UEFI shows USB as first in UEFI boot order. You may want to change that with efibootmgr or from within UEFI's settings (boot menu).
see
man efibootmgr

---

