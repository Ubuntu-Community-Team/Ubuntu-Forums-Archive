---
title: "Gave up waiting for root file system device. ALERT! UUID=xxx does not exist."
date: 2020-12-04
forum: General Help
---

### Post by brian-stl on 2020-12-04
Evening all,


I know what caused the error above I'm just not sure how to fix it.  I created a new software raid array and then deleted it.  But before I deleted it I ran the command "update-initramfs -u".  Now when the system boots I get two errors and it drops to BusyBox initramfs


1. Duplicate MD device names in conf file were found.
2. ALERT! UUID=xxx does not exist. Dropping to a shell!


I know all of my UUIDs, I just dont know what file I  need to edit to make this work.  I tried mdmadm.conf and fstab - no go. What file is feeding this Busybox / initramfs that I need to update with the correct UUID?


Thanks much!
Brian

---

### Post by yancek on 2020-12-05
If you know the UUID for each partition, open the /boot/grub/grub.cfg file and compare the known UUID for the Ubuntu / (root filesystem) partition with the UUID entries in grub.cfg on the appropriate menuentries.

---

