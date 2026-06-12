---
title: "How do i remove window vista completely and remove the memory portion i have?"
date: 2013-03-29
forum: General Help
---

### Post by tahdas on 2013-03-29
The title says it all. How do i remove window vista completely and remove the memory portion i have?

---

### Post by Frogs Hair on 2013-03-29
You could use Gparted from the software center which is a partition tool that allows the  resizing and deletetion of partitions on the harddrive.

Edit: Don't do this if you have used Wubi to install !

---

### Post by tahdas on 2013-03-29
I don't know if i used wubi or not, is there way i can tell?

---

### Post by sudodus on 2013-03-29
Post the output of the command ```
df
```

If there is a /host partition, we can be pretty sure you have a wubi install.

---

### Post by tahdas on 2013-03-29
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda5       11298736 8803984   1920800  83% /
udev             1993352       4   1993348   1% /dev
tmpfs             800436     820    799616   1% /run
none                5120       0      5120   0% /run/lock
none             2001084     492   2000592   1% /run/shm
none              102400      40    102360   1% /run/user

---

### Post by sudodus on 2013-03-29
This looks like a normal installed Ubuntu system with the root partition / on partition number 5 (typically the first logical partition inside an extended partition). So it is not wubi, and you can go ahead with ***gparted*** using Frog's Hair's advice.

But it is always risky to edit partitions (a small mistake will delete valuable data), so you should ***backup*** your Ubuntu partition /dev/sda5 or at least your personal files (documents, pictures etc) before it's too late. There are many threads in the Ubuntu Forums, where we try to help people who did not backup their data ...

---

### Post by tahdas on 2013-03-29
Thanks!

I downloaded gparted, now what do i do?

---

### Post by sudodus on 2013-03-29
Backup

---

### Post by tahdas on 2013-03-29
Check

---

### Post by sudodus on 2013-03-29
Run gparted with superuser privileges

```
 gksudo gparted
```

You can select drive (if more than one) at the top right corner. The GUI is rather self-explanatory. But when you have selected what to do it waits until you click the tick icon near the top of the window.

Be ***sure*** that you can identify which partition you want to remove (the vista partition and maybe the vista recovery partition if you have one).

---

### Post by Frogs Hair on 2013-03-29
Gparted: [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by tahdas on 2013-03-29
When i typed in the command this came up.

---

### Post by sudodus on 2013-03-30
/dev/sda1 is the vista partition and /dev/sda2 is its recovery partition. Click to select them and remove them or resuse them after creating another file system. They seem to be sitting apart from each other, so they can not be merged. This can be checked in more detail with the command
```
sudo fdisk -lu
```
The small partition /dev/sda2 may suit you well as a test partition for new versions or flavours of Ubuntu, while /dev/sda1 can be used for more permanent tasks. If you have no Windows on the computer, I suggest that you create ext4 file systems (format to ext4).

---

