---
title: "root full with emty trash and cache"
date: 2024-06-15
forum: General Help
---

### Post by stevr1it2 on 2024-06-15
Thank you for any help. I have the following situation in my pc created by a technician who is not available anymore

```

sda                       8:0    0  16,4T  0 disk /mnt/Volume_18TB
sdb                       8:16   0   1,8T  0 disk /mnt/Volume_2TB
sdc                       8:32   0   2,7T  0 disk 
&#9492;&#9472;sdc1                    8:33   0   2,7T  0 part 
  &#9492;&#9472;vg_fantec-lv_fantec 252:0    0  10,9T  0 lvm  
sdd                       8:48   0   2,7T  0 disk 
&#9492;&#9472;sdd1                    8:49   0   2,7T  0 part 
  &#9492;&#9472;vg_fantec-lv_fantec 252:0    0  10,9T  0 lvm  
sde                       8:64   0   2,7T  0 disk 
&#9492;&#9472;sde1                    8:65   0   2,7T  0 part 
  &#9492;&#9472;vg_fantec-lv_fantec 252:0    0  10,9T  0 lvm  
sdf                       8:80   0   2,7T  0 disk 
&#9492;&#9472;sdf1                    8:81   0   2,7T  0 part 
  &#9492;&#9472;vg_fantec-lv_fantec 252:0    0  10,9T  0 lvm  
nvme0n1                 259:0    0   1,9T  0 disk 
&#9500;&#9472;nvme0n1p1             259:1    0   121M  0 part /boot/efi
&#9492;&#9472;nvme0n1p2             259:2    0   1,9T  0 part /var/snap/firefox/common/host-hunspell

```

Now i have nextcloud mounted under /mnt/Volume_18TB and i have found it also under media/root/nextcloud and this si filling all my root, the same problem i have with fantec which is under mnt and media. I don't understand why nexcloud and fantec are filling my root even if mounted on 18tb hardisk, and what is wrong. can you help me? thank you

---

### Post by TheFu on 2024-06-16
Need more information.

```
sudo pvs
sudo vgs
sudo lvs

```
commands and output please. Use forum code tags or it will be too hard to read/interpret. The columns need to line up. A select/paste into the forum with code tags wrapped around everything will do that. No need to edit anything to fix spacing/columns.

And if you want to be really nice, The output from 
```
df -hT -x squashfs -x tmpfs -x devtmpfs
lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
```
would be helpful. Forum code tags needed again.  I have suspicions about what they did, but it would be easy to guess wrong without more data.

---

