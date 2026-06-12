---
title: "Wrong Partition Size"
date: 2014-06-02
forum: General Help
---

### Post by Bisneff on 2014-06-02
Hi

These are my partition:

[IMG]https://dl.dropboxusercontent.com/u/41646478/Screenshot%20from%202014-06-02%2019%3A27%3A53.png[/IMG]

I notice that the ext4 partition with the Ubuntu SO is too Big, because I put the /home on another partition. 

Now I want to make the Home partition more large, reducing the / partition. There is a way to do that o I cannot?


Thank You

---

### Post by Impavidus on 2014-06-02
Yes, you can resize. Your only difficulty is that your swap partition gets in the way.

You cannot resize a mounted partition and you cannot unmount a partition when it is in use. So, boot from a live disk and start gparted from there. I think it's installed by default on the live disk. Use gparted to shrink sda5 to something decent. Then right-click on the swap partition and select swap off. Move the swap partition to the left, to put it close to the root partition. Finally expand your /home partition to the left. Relax while the operation is in progress. It will take a while.

Before you start, make sure you have backups of all your vital files. Changing partitions can easily lead to data loss.

---

### Post by Bisneff on 2014-06-06
Thank You for your answer, I'll try soon :)

---

### Post by Bisneff on 2014-06-07
Bump. 

And what is the correct way to enlarge "DATA" instead of Home?

I figured out the best solution could be

/ = 40-50 gb
Home = 120 gb
Data = 409 gb
Swap = 8 gb.

I can do this without data loss, or I've to say goodbye to a bunch of file?

Thanks

---

### Post by Impavidus on 2014-06-07
Why 40-50GB for root? Right now you only use 11GB and the home and data partitions are almost full, so you need everything you can get in those two partitions. 20GB for root should be enough.

Anyway, the procedure is:
A. Make backups of your vital files in /home
B. Boot from the live disk
C. Shrink sda5 (root)
D. Swap off and move sda7 (swap)
E. Move and expand sda8 (home)

sda9 (data) is an ntfs partition, so it may be better to resize it from within Windows, using the unallocated space you created in step E.

You shouldn't loose any files, but it's best to have backups in case something goes wrong. Also, with your drive this full, I think it's time you find some additional storage space. Or delete a lot of old stuff.

---

