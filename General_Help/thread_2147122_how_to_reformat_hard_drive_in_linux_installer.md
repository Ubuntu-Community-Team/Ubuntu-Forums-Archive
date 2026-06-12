---
title: "how to reformat hard drive in linux installer"
date: 2013-05-20
forum: General Help
---

### Post by Ragi1992 on 2013-05-20
Hello all.

I am trying to reformat my hard drive to install windows 7, and the only  option I have left is to use the linux live CD install and wipe it from  there. How would I go about doing it though?

Ubuntu 12.04

---

### Post by oldfred on 2013-05-20
Are you dual booting or just erasing the Linux partitions?

You can use gparted from liveCD or flash drive. Windows only installs into unallocated space with available primary partitions or a primary NTFS formatted partition with the boot flag.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by Ragi1992 on 2013-05-22
This is a screenshot of my gparted :

[ATTACH=CONFIG]242874[/ATTACH][ATTACH=CONFIG]242875[/ATTACH]

I can not unmount or resize any partition at all. Anyone know how to get around this?

---

### Post by coldraven on 2013-05-22
It looks like you are booting from the disc that you are trying to unmount, that is impossible.
You could boot from your live CD, select "Try" then install gparted. It will run in memory. Then use gparted to delete all partitions.
Or download Parted Magic and use that instead. It may come in handy in the future.
[http://partedmagic.com/doku.php](http://partedmagic.com/doku.php)

---

### Post by 3rdalbum on 2013-05-22
The Windows 7 installer can erase disks and contains a partitioner. Why not use that as you are already going to install Windows?

---

### Post by Ragi1992 on 2013-05-22
> **3rdalbum said:**
> The Windows 7 installer can erase disks and contains a partitioner. Why not use that as you are already going to install Windows?

The windows 7 installer will not reformat it since its ext4 format. Windows is kinda picky

---

### Post by jeebustrain on 2013-05-23
> **Ragi1992 said:**
> The windows 7 installer will not reformat it since its ext4 format. Windows is kinda picky

yes it will, you have to delete the partition first.

---

### Post by Bucky Ball on 2013-05-23
To delete your Ubuntu partition you must be running from the LiveCD. It is only logical that you can't unmount the partition you are running from therefore you can't delete it. 

Boot from LiveCD, launch Gparted, right click to unmount any partitions you want to delete (should already be unmounted by default) then kill it. Done.

---

