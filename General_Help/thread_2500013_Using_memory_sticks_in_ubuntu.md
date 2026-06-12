---
title: "Using memory sticks in ubuntu"
date: 2024-08-18
forum: General Help
---

### Post by Tom_Carr on 2024-08-18
How do you change the name of a memory stick?

---

### Post by ajgreeny on 2024-08-18
What do you mean by "the name"?

If you want the named icon for the memory stick in your file-manager to be called something appropriate, eg **music-disk** you simply need to label the partition on the drive.

You can use gparted for this if you need a GUI and I think the disks application can do it but it's something I've never used for that purpose, or if it is an ext2,3 or 4 filesystem you can simply do it in terminal with command ```
sudo tune2fs -L music-disk /dev/sdx#
``` where /dev/sdx# is the memory stick.
See **man tune2fs** for all details.

Probably stick with gparted which you will have to install in your OS or use a live system which contains gparted by default

---

### Post by Tom_Carr on 2024-08-22
I installed gparted and ran it.  I don't see any way to change the name of a memory stick there.

More and more as I age I wonder if I am getting too dumb to use ubuntu.  My 74 year old brain is not what it once was.

---

### Post by Rubi1200 on 2024-08-22
Open GParted >> top right corner there is a dropdown menu for drives.

Is the memory stick displayed there?

If yes, click on it so GParted displays it in full.

You should then be able to change the volume label to whatever you want.

---

### Post by Holger_Gehrke on 2024-08-22
In gnome-disks you just select the device in the left panel, then the partition in the right panel and click the icon of two cogs below the strip that shows the partitions. Select 'Edit Filesystem' from the menu that appears and you will be prompted for a new name for the filesystem. I'm not 100 % certain whether changing the filesystem label while the filesystem is mounted is safe, I usually unmount it before I do this; but then I usually do this from the command line with tune2fs and tune2fs has quite a few other options that are a lot riskier than changing the name and insists on the filesystem not being mounted because of that.



Holger

---

### Post by HermanAB on 2024-08-23
As mentioned above, you need to change the Volume Label of the widget with gparted.

---

### Post by TheFu on 2024-08-23
Label is what you want. Change that to something that fits within the required standards for the file system/partition.  I don't know what those standards are, but I always choose something less than 12 characters, no spaces.  Perhaps I do that just because I remember the old days when 8.3 was the length limitation and that seems to be a common limit for anything touched by MSFT.  

If you use spaces in the LABEL, some commands are harder later, so that's really the only reason NOT to use them.

BTW, read yesterday that lots of older people have their brains improve with age, if they don't have certain diseases. They are better than younger people at all sorts of things and, as expected, practice makes them better.

---

### Post by werewulf75 on 2024-08-26
> **TheFu said:**
> ...Perhaps I do that just because I remember the old days when 8.3 was the length limitation and that seems to be a common limit for anything touched by MSFT.

8.3 limitation didn't happen with Amiga OS since 1984 and IIRC never applied in any *nix/BSD systems from the start. (Never experienced the bad old days of DOS/Win 8/16-bit here, thank goodness. :) )

---

### Post by sudodus on 2024-08-27
¢1. The **name** of a memory stick is hardcoded, and cannot be changed. But you can change the **label**, which is what has already been recommended in previous posts.

¢2. The name and/or model of a memory stick is shown by lsblk as 'model'. The following command line can be useful to view memory sticks, USB drives and other mass storage devices,
```

lsblk -e7 -o model,name,size,fstype,label,uuid,mountpoints

```

---

