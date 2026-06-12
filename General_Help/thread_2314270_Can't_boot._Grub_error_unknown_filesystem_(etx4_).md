---
title: "Can't boot. Grub error: unknown filesystem (etx4 ?)"
date: 2016-02-19
forum: General Help
---

### Post by szymon5 on 2016-02-19
Hello, I have recently installed ubuntu 11.10 on my old laptop and when I try to boot I see:
  error: unknown filesystem.
  grub rescue>
I have 3 partitions: first is ntfs windows xp, second etx4 ubuntu and third swap.
When I use ls command i see:
  (hd0) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1)
so i type: ls (hd0,msdos2) 
  error: unknown filesysem
I get this error with every partiton, one of them is etx4, so it should recongise it and files in it., shouldn't it ?
When I boot livecd, ubuntulive see this partition normally.
I really don't know what to do, since all normal problem solutions doesn't work :/.

---

### Post by oldfred on 2016-02-19
Your 11.10 is long obsolete.
 [http://www.ubuntu.com/](http://www.ubuntu.com/)
Current Releases & Flavors
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
If not wanting to update regularly better to use the LTS, long term support versions released every two years.
If old laptop, you probably need Lubuntu.
[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

Full Ubuntu with Unity is meant for more modern systems. Often Unity is the issue as it required a better graphics system.
I am running Ubuntu 12.04 on a almost 10 year old laptop. But Unity will not run, but I install fallback which is like the old version of Ubuntu with gnome2.

---

### Post by szymon5 on 2016-02-22
I have tried newer versions but they don't want to work because my laptop doesn't support pae. I'm pretty sure that it isn't caused by unity or lack of performence. I installed other linux distibutions, and had the same issue. It's like problem with booting only, livecd works 100% properly. When  I restore windows bootloader to mbr, windows boots without problems, then i install grub and againt it can't see filesystem.

---

### Post by oldfred on 2016-02-22
I though Lubuntu handled PAE correctly, still.

Where on drive is Linux partition?
Some old BIOS only boot from files fully inside first 137GB of drive. So / (root) must be fully inside the beginning of drive and rest as /home or a separate /boot that is fully inside the first 137GB.

Post this from live installer.
sudo parted -l
sudo fdisk -lu

---

### Post by mörgæs on 2016-02-23
Here's a guide for getting Lubuntu 15.10 or 14.04.4 to work on hardware without PAE:
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

---

### Post by szymon5 on 2016-02-23
I'll try Lubuntu and your commands when I back to home, but it seems like it's problem with bootloader only and harddrive has a capacity of 20 gb :D.

---

### Post by mörgæs on 2016-02-24
20 GB is plenty.
Are you sure that you want to keep the unsupported XP? It's a security breach, even more than when it was supported.

---

### Post by szymon5 on 2016-02-25
I need this windows for a few next weeks, and then I'll do total disk format, maybe this will help.

---

### Post by mörgæs on 2016-02-25
It will at least be easier to install a single boot Buntu than a dual boot.

---

### Post by szymon5 on 2016-03-04
Okey, after format it still didn't want to work, like 3 diffrent errors :D , but finally after a few formats, and making special partition for /boot at the start of disk it finally works.

---

