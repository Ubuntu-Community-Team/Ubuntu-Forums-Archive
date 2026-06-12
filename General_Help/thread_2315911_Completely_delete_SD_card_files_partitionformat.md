---
title: "Completely delete SD card files partition/format"
date: 2016-03-03
forum: General Help
---

### Post by Bowei_Zhao on 2016-03-03
[COLOR=#111111][FONT=Ubuntu]I'm having issues doing a legit format and partition of an SD card on Ubuntu I have plugged in.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I've been using fdisk, mkfs, Disks, and GParted but they have all only 'done' the task and not deleted the files.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I'm using fdisks and mkfs initially to delete,make,and later put files onto the SD card to make a bootable Os for another system.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]It works fine but the files I had on it before STAY there and won't come off.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I need to use sudo to run the commands so I can't modify any of the files once mounted. I've tried chown and chmod and then rm -rf but none of them work to delete any files.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]The only way it seems to delete my files is to do a complete zero erase of the drive which takes about 15minutes.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Is there a better way to do this? I wouldn't even mind graphically deleting the files but I am not allowed to as it won't give me permission.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Thank you[/FONT][/COLOR]

---

### Post by QDR06VV9 on 2016-03-03
I have found that for what ever reason..sometimes you have to boot to a tool(CD, DVD, USB) like gparted or any other medium to perform the needed action.
Then just point it to the SD card and format. It has never failed me with that procedure.
Good Luck..

---

### Post by Bowei_Zhao on 2016-03-03
> **runrickus said:**
> I have found that for what ever reason..sometimes you have to boot to a tool(CD, DVD, USB) like gparted or any other medium to perform the needed action.
Then just point it to the SD card and format. It has never failed me with that procedure.
Good Luck..

Formatting isn't the problem, nor is deleting. It does this.

But I have to next use fdisk again to make a new partition and guess what shows up when I do? My old files :(

---

### Post by coldraven on 2016-03-03
Try using the wipe function in mkusb to wipe the first MiB. Then use gparted to create a new whole drive partition and format it FAT32
This has worked for me in the past.
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by QDR06VV9 on 2016-03-03
> **Bowei_Zhao said:**
> Formatting isn't the problem, nor is deleting. It does this.

But I have to next use fdisk again to make a new partition and guess what shows up when I do? My old files :(
Why do you have to use fdisk?? Just create the partition after formatting using the live medium..
I can only show you the water it is up to you to take the plunge..
Kind regards

---

### Post by sudodus on 2016-03-03
Sometimes you need to ***unplug and replug*** a USB device for the system to recognize the changed partition table and file system.

***Unmount:*** Always make sure that all partitions on the USB device are unmounted before you unplug it. Otherwise the file system might be corrupted.

---

### Post by Bowei_Zhao on 2016-03-31
It seems there  was dual issues that happened.

First due to locking of R/W of the drive, sometimes the commands  wouldn't run correctly and I assumed they went through.

The next is that I got the display refresh bug where Ubuntu 14.04 doesn't 'refresh' Nautilius File Manager and still shows me  and allows access to the file tree making it appear as  if the  files did not dissapear.

---

