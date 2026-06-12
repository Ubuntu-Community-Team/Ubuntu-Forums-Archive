---
title: "[SOLVED] Unistall 7.04"
date: 2007-07-13
forum: General Help
---

### Post by djhvt on 2007-07-13
In order to give Ubuntu a try I installed it as a partition on my main computer. I was pretty darn impressed and have decided to use it as the sole operating system on my new computer I am building. This leaves me with an issue: how do i remove 7.04 from my older machine so I can continue to run the basic Windows 2000 pro stuff I need for work?

Here is the catch though, I no longer have the restore disk for Windows. Also leaving it on is not a option as the system has limited resources and i have some new software i need to run on it on top of whats already on there. My work is supposed to give me one of the XP computers they have, but who knows how long it will take for that to happen.

In retrospect i probably should have just put it on my new computer, but live and learn i guess lol

thanks for all the great work everyone does here at Ubuntu

p.s. why the heck are the forums so slow? It takes forever for the pages to load, but only the forum pages everything else loads just fine....

---

### Post by lisati on 2007-07-13
I'm not sure about recovering the Windows stuff without the benefit of recovery disks or backups - anyone? 
Possibly the slow forums is because it can get rather busy here.

---

### Post by djhvt on 2007-07-13
My windows install works just fine and i have no problem booting into it, i just need to remove Ubuntu for storage purposes. So its not so much recovering windows but rather removing ubuntu that is my issue

---

### Post by merlinus on 2007-07-13
The gparted live cd may work for this.

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

You can delete your ubuntu partitions, format them as ntfs, and then re-size your windows partition to include them.

You may then have to restore the windows bootloader,  SuperGrub can do that for you:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

---

### Post by dagnabit dang doohickey on 2007-07-13
Using a Win98SE-OEM boot disk is probably the easiest way to do this.

HowTo:
[http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_98_Floppy_Disk_Method]("http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_98_Floppy_Disk_Method")

Bootdisk download page:
[http://www.bootdisk.com/bootdisk.htm]("http://www.bootdisk.com/bootdisk.htm")

And then just delete/reformat the offending partitions with Windows Disk Manager on your next boot into Windows.

---

