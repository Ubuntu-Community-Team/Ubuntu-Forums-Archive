---
title: "Copying from an old disk to a new disk"
date: 2008-06-09
forum: General Help
---

### Post by Arneu on 2008-06-09
Deleted post

---

### Post by Gannon8 on 2008-06-09
I just did this last night. How ironic.
Here's what I did, I assume you can have both devices connected to the computer at the same time, and the new drive has not been formatted.
1. Boot Ubuntu from the LiveCD
2. Open GParted (System > Administration > Partition Editor), wait for the program to scan your disks
3. On the upper right corner, there should be a drop down box with your dirve's file on it. Click it, and select your old drive.
4. Right click on the partition you want to move first (preferably, the first one listed) and select copy.
5. Go to the new drive, and right click on the unallocated space. Now select Paste. If you want to resize the partition, you can.
6. Repeat steps 3-5 for all other partitions you want to move.
7. Click Apply, and wait for it to complete.  Depending on the size of your partitions this will take a LONG time. If you are copying an NTFS filesystem, then you will not get a progress bar.
8. When it is finally done (you may want to leave your computer on overnight), right click the partition with GRUB on it, and select Manage Flags.
9. Check the "boot" flag.
10. Exit GParted, unmount the old disk, and open a terminal.
11. Run these commands to get GRUB back:
```
sudo grub
find /boot/grub/stage2
```
Use what this command gives you for the next commands, it should be something like (hd0,0) or (hd0,1)
```
root (hd?,?)
setup (hd?)
quit
```

After that, reboot your computer to the new drive, and it should work. If you boot into windows, it may run chkdsk because the partition changed.

---

### Post by Gannon8 on 2008-06-09
> **Arneu said:**
> Deleted post
To mark a thread as "Solved," go to Forum Tools > Mark Thread as Solved.
It lets other people who have the same problem use this thread, and it lets other people know that this solved your problem.

Thanks for the thanks though :)

---

