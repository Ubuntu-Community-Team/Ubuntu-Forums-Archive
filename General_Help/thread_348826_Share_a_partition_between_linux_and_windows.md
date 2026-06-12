---
title: "Share a partition between linux and windows"
date: 2007-01-29
forum: General Help
---

### Post by mrwooster on 2007-01-29
Hi,

I have a dual boot Drapper - WinXP system. The winXP system uses NTFS so I can't write to the windows partition and windows does not even wan't to know about Linux. When I installed linux i created an extra little partition /documents which I wan't to be able to access from both windows and linux. Currently the type is ext3 and so it is not recognised by windows. Is there a way of reformatting that specific partition (obviously destroying data on /documents but keeping all other data on other partitions) so that I can write to it from both windows and linux? Maybe use FAT32 ....

Please don't suggest anything which would cause any risk to the system (windows or linux), I only wan't to do this if it is completly (obviously within reason) safe.

Thanks

Guy

---

### Post by vigleik on 2007-01-29
There's a driver for writing to NTFS file systems called ntfs-3g, and while it's still in beta the developers claim it's already very stable. Also, I believe it's possible to install a windows driver to access ext3 file systems (google for it).

Anyway, you can easily reformat that specific partition to FAT32 if you want, and that's the easiest way to make sure the partition can be accessed by any operating system. The easiest way (after backing up the data on that partition, because all data on it will be lost) is to boot from the live CD and use gparted (or qtparted?). You could also do this without the live CD, after installing gparted or qtparted. Just make sure you unmount the partition first.

---

### Post by x64Jimbo on 2007-01-29
There's also an ext3 filesystem driver for windows - FAT32 is NOT a journaling filesystem, so files stored in it are much more prone to corruption. Avoid it at all costs. I recommend ntfs-3g first because it has native journaling support. Then the [http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html) driver because it mounts the partition as ext2, which is also non-journaled, but less vulnerable to corruption than FAT32. Good luck.

---

### Post by gwpritch on 2007-01-29
I would be very careful using the ext3 driver for windows. If you look around this forum you will find several posts from users who have tried it and had some degree of file corruption on their ext3 partitions. I have used a shared fat32 partition for several years with no problems what so ever. 
You also have to realize that the windows driver does not preserve permissions so if you do decide to go that route, under no circumstances allow your root partition to be accessed.

---

### Post by strabes on 2007-01-29
I've been using the fs-driver for months and haven't had any problems. It's kind of up to you what to do.

---

