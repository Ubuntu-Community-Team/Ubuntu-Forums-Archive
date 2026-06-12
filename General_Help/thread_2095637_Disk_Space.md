---
title: "Disk Space"
date: 2012-12-17
forum: General Help
---

### Post by tonaves on 2012-12-17
Hi

Can anyone help me get more disk space available on Ubuntu? I have loads of spce free on my desktop but i cant seem to acess it from Ubuntu.
Thanks

---

### Post by Impavidus on 2012-12-17
Do you have ubuntu only on your desktop (probably not), a dual boot alongside another operating system (windows for example) or a wubi install?

---

### Post by Frogs Hair on 2012-12-17
Hello and Welcome

If you have a traditional dual boot and not a Wubi installation, install Gparted from the software center and then you can do some research on how to re-size the partition.

There are plenty of forum members who have used the application that can help. :)

---

### Post by Mark Phelps on 2012-12-17
> **tonaves said:**
> Can anyone help me get more disk space available on Ubuntu? If you installed Ubuntu to its own partition, you would have to remove space from a partition adjacent to it, boot from a CD (because you can't mess with a partition while you're using it) and then enlarge the Ubuntu partition to absorb the free space.

If you're running a system that also has Win7 on it, and you want to shrink that, do NOT use GParted or any other Linux utilities to do that; instead, use the Win7 Disk Management utility.

> I have loads of spce free on my desktop 

A "desktop" is at most a folder in the Ubuntu file system -- and it doesn't have space allocated to it.  So, where is this "loads of space" actually located?

---

### Post by tonaves on 2012-12-17
Indeed i have windows and ubuntu systems working. 
I have 4 partitions on 2 disks, and i need to use one of those partitions to install a game and i cant acess it.

---

### Post by Impavidus on 2012-12-18
What kind of partition is it, the one on which you want to install that game? Linux (ext2, ext3, ext4), windows (NTFS), fat, something else? Can you see that partition in windows? Can you see it in ubuntu disk management tools? Do you currently use that partition in windows?

Assuming that you you checked the game will run on linux (of course, else you would install it on your windows partition), it probably works best if installed on a partition that knows about permissions. There will be an executable in it, maybe score files that can be edited by the game but not by the user, maybe it wants a secure system to download and install additional content from the web. That means it has to be a linux partition (ext3 or ext4). If the partition in question is of another type you will have to format it. If you use it for storing windows files too, you will have to split the partition in two, keeping one part NTFS and making a new part ext4.

Once you have prepared the partition you have to configure your system so that it mounts the partition where you like it (edit /etc/fstab). Then, install your game there. You can also try and merge it with your current / partition (provided it's on the same disk), but keeping it as a separate partition is only slightly less flexible and saves you from the hazards and difficulties of modifying the root partition.

Don't be afraid, it's certainly doable. We're waiting for further questions.

PS: I assume desktop means desktop computer, as opposed to laptop.

---

