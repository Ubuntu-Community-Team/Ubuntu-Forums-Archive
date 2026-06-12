---
title: "Partition problem."
date: 2014-12-22
forum: General Help
---

### Post by kosimiki on 2014-12-22
Well i installed first Ubuntu for learning purposes. At that time i did not think that 40 GB will not be enough. Now i don't know how to extend it :S
[IMG]http://www.kepfeltoltes.hu/141222/K_perny_k_p___8211__2014-12-22_12_59_20_www.kepfeltoltes.hu_.png[/IMG]

---

### Post by ajgreeny on 2014-12-22
You don't have many options as there are only really two things you can sensibly do.

1 - Reinstall and take more of sda3, plus the 19.53GB unallocated between sda3 and sda4 for your Ubuntu installation.

2 - Use gparted on a live system to shrink sda3 and then move and stretch sda4 to fill all the space at the end of the drive.  This will probably take a long time as gparted will do a filesystem check of the ubuntu partition before it starts to move and enlarge it and then will repeat the check again after it finishes doing this.

I assume sda1, sda2 and sda3 are all windopws partitions and that sda2 is the OS itself.  Which version of Windows is it?

Make sure whatever you do that you have good and complete backups of all important personal files.

If sda3 is just a data partition are you are aware that you can read and write to that partition from ubuntu, and it is very easy to set it up to be mounted at boot with read/write permissions and to link your current ubuntu /home folders to similar folders in that ntfs data partition.  That may mean that all this partition editing is not necessary at all and you can overcome your problems with edits to a few files in the ubuntu filesystem and making a few links to existing folders.

---

### Post by kosimiki on 2014-12-22
I use windows 8.1. 
The broblem is that i can't do anything with sda4 everything is grey. The current unallocated space was part of sda3. I prefer extending  the ubuntu partition. I dont want the 2 things mix because one is for education and windows mostly for games.

---

### Post by raptir on 2014-12-22
You won't be able to modify sda4 while you are running Ubuntu since it is the partition Ubuntu is installed to. You can only modify inactive partitions (partitions that aren't mounted). If you still have the Live disc (DVD or flash drive) you used for installation, you can boot into that and use gparted from there. Otherwise, GParted offers live CDs as well that are a smaller download.

[http://gparted.org/livecd.php/](http://gparted.org/livecd.php/)

---

### Post by grahammechanical on 2014-12-22
The unallocated space is 19.5GiB in size. What is stopping you from expanding sda4 into the unallocated space. Answer = everything is grey. Do you notice the little key icon alongside /dev/sda4? That tells us that sda4 is mounted. Are you running Gparted from your installed Ubuntu? Run it from a live session and unmount sda4.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

> [COLOR=#000000][FONT=Bitstream Vera Sans]To unmount a partition:[/FONT][/COLOR]
[COLOR=#000000][FONT=Bitstream Vera Sans]
[LIST]
[*]Select a mounted partition. See [the section called &#8220;Selecting a Partition&#8221;]("http://gparted.org/display-doc.php?name=help-manual#gparted-select-partition").

[*]Choose: Partition &#8594; Unmount. The application unmounts the partition from the mount point and refreshes the device partition layout in the gparted window.
[/LIST]
[/FONT][/COLOR]


[http://gparted.org/display-doc.php?name=help-manual](http://gparted.org/display-doc.php?name=help-manual)

Regards.

---

### Post by kosimiki on 2014-12-26
Thank You! I used Gparted live on my usb drive it took like 40 mins or so but now everything is ok.

---

