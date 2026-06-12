---
title: "Erase flash drive"
date: 2016-05-06
forum: General Help
---

### Post by Rixter69 on 2016-05-06
Hey All:

   I saw there was a Ubuntu/Linux forum before I logged in, now I can't find it??? I'm going to ask my question and if this isn't the appropriate forum, then an *admin* can move it to the correct forum. I'm needing to "wipe" a flash drive (Leaxar 16Gb) so that I can use it again. Somehow it got 'write protection" installed on it (had it in a Win7 machine) and now it needs a complete wipe for I've done everything I've found to try to remove the write protection and all have failed. Now, let me explain this, I've done everything I could find to use according to Win7...I've not tried a Linux approach. I have two questions therefore: #1. Does Linux incorporate a program that will completely wipe this flash drive? #2. I was going to use DBAN but then read where it is not always so successful with flash drives? I'd like to here from those who are versed in this operation (flash drive erasure). I have used DBAN in the past and was highly satisfied with it's performance, but then, that was on a number of HDD's. Did not even guess it wouldn't work as well on flash drives (pendrives/USB drives/ jumpdrive, etc...) Also, I was told that Linux "reads" differently than Windows and, therefore, the drive might not read "write protected" or may be able to be easily erased/formatted using a Linux program? Either way is fine with me, just so I can once again, use the drive in a read/write manner. Comments on the DBAN and also the Linux methods would be most appreciated! The drive is formatted in FAT32. Please, do not waste my time nor yours with a _*stupid*_ suggestion such as "Throw it(the flash drive) away..they're so cheap nowdays".
Thanx:
[SIZE=5][FONT=times new roman]***Rick***[/FONT][/SIZE]

---

### Post by Geoffrey_Arndt on 2016-05-07
Just use the "gparted" program to reformat the usb flash-stick.   Be sure to format it FAT32 if you want to use it without worrying about Linux permissions.

---

### Post by poltiser2 on 2016-05-07
I use disk (gnome-disks) - upper menu format option...
I use as well mint-stick...
In desperation - I learn cli - command

Good luck

---

### Post by DuckHook on 2016-05-07
As it happens, this same question was asked two days ago on [this]("http://ubuntuforums.org/showthread.php?t=2323400") thread. Skip to the recommendations towards the end of the thread involving the use of *dd* and *mkusb*.

---

### Post by sudodus on 2016-05-07
I agree with *DuckHook*.

If you are lucky, you can wipe the first megabyte and create a new partition table (only in special cases the whole device) with mkusb, using dd under the hood.

But the pendrive might be gridlocked, and then I know no tool, that can make it writable again. See these links for more details

[Pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")

[Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

***Edit:*** There might be a small mechanical switch, that can switch between read/write and read-only.

---

### Post by Rixter69 on 2016-05-08
To: [[COLOR=#000000]Geoffrey_Arndt[/COLOR]]("http://ubuntuforums.org/member.php?u=1973436")

   Thank You for replying. I was told Linux "reads" in a different manner than MSWin. Could it be that Linux would not "see" this drive as write protected?. Or, is it just that Linux is more powerful when it comes to formatting/erasure of data? In any way, will formatting with Linux remove the write protection, as that is what my main objective is?
Stay Sharp:
[SIZE=5][FONT=times new roman]***Rick***[/FONT][/SIZE]

---

### Post by Rixter69 on 2016-05-08
Sudous:

  Thanx for the reply. I'll read the "links" and hopefully wise up enough to fix my problem.
[SIZE=4][FONT=times new roman]***Rick***[/FONT][/SIZE]

---

### Post by Rixter69 on 2016-05-08
[I][B]DuckHook

 [/B][/I]  Did not see that post?? Will go looking for it. Just wondering ...if Linux will erase the drive then there's no need to go further, however, I should have been a bit more clearer. The main objective is to _remove the write protection_ on the drive. But, whatever method(s) will do the trick is just fine!
[SIZE=4][FONT=times new roman]***Rick***[/FONT][/SIZE]

---

### Post by Rixter69 on 2016-05-12
Hey Geoffrey:

  When I get to use a Linux machine, I'll do that (?). Just want to let you know that Win7 will NOT allow a "format" nor deletion of, nor addition of files to the drive. and, yes, it is/has been formatted in FAT32 as are all my pendrives.

[SIZE=4][FONT=times new roman]***Rick***[/FONT][/SIZE]

---

### Post by Geoffrey_Arndt on 2016-05-13
So, per post#5 - - you are sure there is no mechanical switch or toggle on the pendrive for write protect . . . . ?

Also, write protect is kind of a generic non-OS term - - in Linux terms, native Linux file systems will "protect" the files from write via the Linux permissions system.   In other words, if you use gparted to format the pendrive as ext4 (a Linux File System),  it would be owned by "root" and essentially locked down unless you use Linux CLI commands to change ownership.

---

