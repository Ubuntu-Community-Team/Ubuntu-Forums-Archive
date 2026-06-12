---
title: "expanding vm LVM"
date: 2022-06-02
forum: General Help
---

### Post by sniper8752 on 2022-06-02
How would I go about expanding the following root lvm:
```
NAME                        MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda                           8:0    0  132G  0 disk
&#9500;&#9472;sda1                        8:1    0    1G  0 part /boot
&#9492;&#9472;sda2                        8:2    0   31G  0 part
  &#9500;&#9472;rl_new--confluence-root 253:0    0 27.8G  0 lvm  /
  &#9492;&#9472;rl_new--confluence-swap 253:1    0  3.2G  0 lvm  [SWAP]
sr0                          11:0    1  1.9G  0 rom


```

---

### Post by TheFu on 2022-06-02
We need to see the output from 
```
sudo pvs
sudo vgs
sudo lvs
sudo parted -l /dev/sda

```
to know if it is even possible.
Use forums code-tags. Don't make it hard to help you, please.

---

### Post by Dennis N on 2022-06-03
Here's my take on your situation:

Looking at your display in post #1, you have plenty of space on the disk (132G). Your volume group uses sda2, but is only ~31G. To expand your 27.8G root logical volume, you can add a new partition, and then using **gparted** format it as **lvm pv** to create an new physical volume. Then use **vgextend** to add the new physical volume to your volume group. Finally, you use **lvextend** to enlarge the root logical volume by some amount (be sure to include the --resizefs option with this). The specific command options and values I leave to you. I assume you would be familiar with these commands.

---

### Post by TheFu on 2022-06-03
The OP has reposted the same question at least 3 times and hasn't responded back to this thread, which was the first. Feels like we're being played.

---

### Post by sniper8752 on 2022-06-03
You can delete those.  The submit of the question did not go through, so I refreshed the page, and it failed to load.  
Will post those output soon.

---

