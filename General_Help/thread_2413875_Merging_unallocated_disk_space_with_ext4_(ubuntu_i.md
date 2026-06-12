---
title: "Merging unallocated disk space with ext4 (ubuntu installed)"
date: 2019-03-03
forum: General Help
---

### Post by snbn on 2019-03-03
So I merged an 80 GB unallocated disk space to my Ubuntu partition in Windows Partition software (I came from windows environment), the merge is completed successfully, but when I check my disk size in my Ubuntu using Disks, the disk size increased but the 80 GB that I just merge is somehow occupied. It says 54% full. And I only have 73 GB of free space which was my previous free space before I merge. Basically I still have the amount of free space before and after I merge my disks.
Is there any way I can fix this?
Below is the screenshot of my harddisk
[IMG]https://i.stack.imgur.com/cmIXs.png[/IMG]

---

### Post by yancek on 2019-03-03
Boot Ubuntu, open a terminal and run the following command and post the outut here.  That's a lower case Letter L in the command:

```
sudo parted -l
```

---

### Post by HermanAB on 2019-03-03
Bear in mind that faffing with partitions is an almost sure fire way to lose all your data...

---

### Post by snbn on 2019-03-03
here's the result sir
[IMG]https://i.ibb.co/JcBF9kv/image.png[/IMG]

---

### Post by snbn on 2019-03-03
Update: sudo resize2fs /dev/sdb3 solves my problem

---

