---
title: "Ubuntu got my PC messed up for good."
date: 2008-06-12
forum: General Help
---

### Post by Qbit123 on 2008-06-12
Okay, so. When i got the Ubuntu live CD (Im using it now) i was like "Wohoo", but then, i booted with it. Everything went fine sept i could not use any effects or the screen would fill up with black/grey/white pixelated boxes. Well i tought that it would go away when installed. Well apparrently not, then i got problems with ATI Radeon X700SE.. I just had to install Windows back again even tough i wanted to use linux, well i had an CD from Acer that would install Windows + Drivers, went fine until i booted up. GRUB Kept keeping me errors, so back tot the internet. I searched for help, everybody said to use fixmbr on the recovery console from the original WIndows XP CD, so i got the Windows XP CD (100% Real, non pirated) I booted up with it, then
when it said something familiar to "Checking System info" etc. it goed to a black screen and nothing happens, i waited 4h, no response form my PC. i used 2CD's one with SP1 and one with SP2, also when i installed Ubuntu in "Use the whole drive" etc. cause that was in Finnish (Yea, I'm from Finland).

Please help me, quick. I'm addicted to my PC. And i promise ill install Ubuntu to this PC When i get a new one.

---

### Post by SyL on 2008-06-12
Hi,

are you able to do a scan disk once you have booted on the Windows CD?





Syl

---

### Post by Qbit123 on 2008-06-12
Nope, i cant do anything. THe LiveCD Is the only thing I can use.
ONly the disc from Acer works but i cant boot from it because its not a normal Windows XP install CD its an intaller Acer & Symantech made. :(

---

### Post by SyL on 2008-06-12
> **Qbit123 said:**
> Nope, i cant do anything. THe LiveCD Is the only thing I can use.
ONly the disc from Acer works but i cant boot from it because its not a normal Windows XP install CD its an intaller Acer & Symantech made. :(


Do you mean Windows LiveCD? or Ubuntu one?

---

### Post by Qbit123 on 2008-06-12
The Ubuntu one.

---

### Post by tbehrens on 2008-06-12
Don't freak out.  All that has happened is that GRUB was added to your MBR and is now looking for your old ubuntu install.  What you need to do is format the drive completely and use your rescue CD again and all should be fine.

---

### Post by SyL on 2008-06-12
then look at this thread


[http://ubuntuforums.org/showthread.php?t=827108](http://ubuntuforums.org/showthread.php?t=827108)

---

### Post by Qbit123 on 2008-06-12
Well, do i need to use the partition editor. I have: /dev/sda1 and sda2, sda1 is FAT32, I tried NTFS Too.. But im shcoked cause i used 2 Windows XP Install CD:S and both of them freezed after "Looking up system info" or somethinf familira.

---

### Post by Qbit123 on 2008-06-12
> **SyL said:**
> then look at this thread


[http://ubuntuforums.org/showthread.php?t=827108](http://ubuntuforums.org/showthread.php?t=827108)

Din't help at all.

---

### Post by issih on 2008-06-12
alternatively get hold of supergrub and burn that to disk, if that can boot it can fix the mbr for you.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by summuner848 on 2008-06-12
Do you have a second partition on your hard disk that includes a windows installer? or something along the lines of "Startup fixer thing: Fix problems that cause windows to fail to start."

Because I have a Compaq Presario with Vista installed and it came with a second partition that can reinstall vista at any time as long as i boot to the second partition (F8 at startup)

I've had to fix grub boot loader before. All i did was back-up all my stuff to my external HD and reinstalled windows via the second partition

---

### Post by tbehrens on 2008-06-12
You might try to DL the UBCD (Ultimate boot CD) and wipe the drive.  This will overwrite the whole disk and you should be able to reload windows.  As far as Ubuntu goes did you try any of the work arounds for ATI cards?

---

### Post by SyL on 2008-06-12
> **Qbit123 said:**
> Din't help at all.



Windows installation CD should not care at all about what is installed on your disk, nor about the partition format. As long as the CD is can recognize your disk, you should then be able to delete the existing partition and create new NTFS one for windows ...

---

### Post by SyL on 2008-06-13
Hi Qbit123,

How is it going?
So if windows is not able to see your disk or if what is on the disk make it crash, you should totally clean your disk using different tool, that why i was referring to this post [http://ubuntuforums.org/showpost.php?p=5171941&postcount=2](http://ubuntuforums.org/showpost.php?p=5171941&postcount=2)

Hope you will get it work!

---

