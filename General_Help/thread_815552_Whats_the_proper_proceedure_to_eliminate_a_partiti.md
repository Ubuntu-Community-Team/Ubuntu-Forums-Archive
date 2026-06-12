---
title: "Whats the proper proceedure to eliminate a partition?"
date: 2008-06-01
forum: General Help
---

### Post by sofasurfer on 2008-06-01
Say I have an extra partition on my hard drive that I use for what ever.

When I created the partition and mounted it I followed these steps...

1) Create partition using Gparted.
2) Edit fstab file to show new partition.
3) Create directory for new partition with "mkdir /media/<partition name>"

Now suppose I want to eliminate the partition. Do I need to...

1) Delete directory with "rm -R /media/<partition name>"?
2) Delete or comment out the entry in the fstab file?
3) Delete the partition using Gparted?

Or is it easier than that?

---

### Post by logos34 on 2008-06-01
2) & 3) are the most important (otherwise the system will throw an error looking for missing partition to mount at startup).  But you might as well delete the folder/mointpoint too, unless you want to perhaps mount another partition there.

---

### Post by Lord Xeb on 2008-06-01
When you make a partition with gParted, you do not need to edit fstab. Just restart your computer or log out, then back in. Your system should be able to view that partition. 


You should just be able to delete the patition using gParted.

---

### Post by sofasurfer on 2008-06-01
>When you make a partition with gParted, you do not need to >editfstab. Just restart your computer or log out, then back in. >Your system should be able to view that partition. 

Really!!??
Thats fasinating. I will try that after I remove the partition and create a new one. And "No" I am not performing needless steps. I am learning in my own way, therefore, "delete and recreate". Thanks.

---

### Post by Lord Xeb on 2008-06-01
Just remember, do not pick the wrong partition. Also, make sure all the extra fstab entriers are removed and anything extra you did for that partition removed aswell. This will prevent error messages.

---

### Post by logos34 on 2008-06-01
> **Lord Xeb said:**
> When you make a partition with gParted, you do not need to edit fstab. Just restart your computer or log out, then back in. Your system should be able to view that partition.

right, it will mount as '/media/disk', '/media/disk1', etc. when you click on it.  But if you want it to mount at a predefined directory (the normal setup) then you need to edit fstab.

---

### Post by fragos on 2008-06-01
Definitely do #3 1st. The others may not be necessary but it's easy enough to check after deleting the partition with Gparted.

---

