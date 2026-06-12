---
title: "After moving /home to a new drive need help merging the old /home space to /root"
date: 2016-03-03
forum: General Help
---

### Post by mehdi_azzad on 2016-03-03
I have successfully moved my /home folder to a 2[SUP]nd[/SUP] hdd  (sdb) and everything is working fine. Now, I would like to reclaim the space in the in sda where the old /home used to be and merge the space with /root.
I know it can be done using gparted but I’m not sure how.
Any help is appreciated.

---

### Post by oldfred on 2016-03-03
Was old /home a folder inside / (root) or a separate partition?
If a folder, you would not use gparted. If a partition then you can use gparted.

Post these:
sudo parted -l
df -h
cat /etc/fstab

---

