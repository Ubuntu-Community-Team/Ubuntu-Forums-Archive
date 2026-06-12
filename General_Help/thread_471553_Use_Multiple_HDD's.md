---
title: "Use Multiple HDD's"
date: 2007-06-12
forum: General Help
---

### Post by Testarosa on 2007-06-12
Hi, I am new whit UBUNTU and have a question. 

I have 3 HDD's, and i installed UBUNTU on the first hdd. But now i want UBUNTU to reconize the other 2 hdd's. Where en how can i find that?

I have 3 x 400 GB Samsung HDD's.

Thanks in advance:D

---

### Post by Mr. C. on 2007-06-12
From the command line, see if this shows the disk:

```
fdisk -l /dev/hdb /dev/sdb
```

If either is found, try also the hdc or sdc variant.

Have you created partitions on the disk or formated a file system ?

MrC

---

### Post by vanadium on 2007-06-12
IT is a good idea to post such questions in the Beginners forum. You do not tell how these disks are connected. USB drives should automatically appear as an icon on the desktop. Internal drives are normally recognised during the installation and also mounted under /media (= icon on the desktop). Thus, it is not quite clear to me why you would not see these drives.

First indeed check whether the extra disks are seen. To do that, post the output of the following command here:

```

sudo fdisk -l

```

This version of the command will simply list all drives with their partitions. If your drives are on there, you can continue. Else your drives are not properly connected.

Next check what is mounted:

```

mount

```

(post the output here) Perhaps you'll see that your drives are already mounted. The entry after "on" in the above command will tell you where in the file system the drives are mounted (if they are).

If they are not mounted, you will need to mount them yourself. To automatically mount them, you will need to add a line in /etc/fstab (post the output here).

With all this output, we will be able to see what is wrong, and eventually what can be done about it.

---

