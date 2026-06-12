---
title: "How to burn image to SD card?"
date: 2013-01-12
forum: General Help
---

### Post by jfever311 on 2013-01-12
Hey folks, I am in the process of adding Google Play and some doing some other tweaking to my kids tablets and my wifes Nook HD. In order to do the mods I need on the Nook HD, I need to write an CWM image to an SD card. With windows I know I could use Win32DiskImager to do this. I am running Ubuntu 11.10 though, and I cannot figure out how to do burn the files I need to the SD card and make it bootable. I am not an hardcore computer guy, but with some patience and maybe some guidance, I think we can get this done. Here is a link to the thread I am using on [COLOR=Red][XDA forums]("http://forum.xda-developers.com/showthread.php?t=2062613&highlight=ubuntu")[/COLOR]. Maybe someone on here can help me out on this. Thanks in advance.

Jason

---

### Post by Cheesemill on 2013-01-12
You can use the dd command.

First a warning, by selecting the wrong device it is easy to overwrite your hard drive by mistake, make sure you know which drive is which.

To find out which drive is your SD card you can use the fdisk command...
```
rob@arch:~$ sudo fdisk -l

Disk /dev/sda: 64.0 GB, 64023257088 bytes, 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   125045423    62522711+  ee  GPT

Disk /dev/sdb: 320.1 GB, 320072933376 bytes, 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1   625142447   312571223+  ee  GPT

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes, 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  1953525167   976762583+  ee  GPT

Disk /dev/sdd: 8011 MB, 8011120640 bytes, 15646720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048    15646719     7822336   83  Linux
```By looking at the size of your drives you can easily see from the size which your SD card is. In my output you can see I have an 8GB SD card called /dev/sdd

Then to write the image to your card you would use...
```
dd if=~/filename.img of=/dev/sdd
```This is assuming the image is called filename.img and it is in your home folder, adjust your path and filename to suit.

An explanation - all dd does is copies data from one place to another. All you need to do is specify the input (if=) and the output (of=).

---

### Post by jfever311 on 2013-01-12
Permission Denied?!?! I followed the steps you listed and this what I got. Any ideas? Matter of fact, let me do it all again and get you a screenshot.

---

### Post by jfever311 on 2013-01-12
Screenshot..
.
.

---

### Post by Cheesemill on 2013-01-12
Sorry, that's my fault.

You need to type sudo in front of the dd command...
```
sudo dd if=~/NookHD-bootable-CWM-6025-for-emmc-stock-4GB-rev2.img of=/dev/mmcblk0
```

---

### Post by jfever311 on 2013-01-12
Okay, I did that. It asked for my password, I entered it, and it is just sitting here at this point. The cursor will flash ten or so times and then stay solid for a few seconds. If I try to exit out I get this....
.
.
.

---

### Post by jfever311 on 2013-01-12
Of course, the file is 4gb, so I reckon it could take a few minutes, right?

---

### Post by jfever311 on 2013-01-12
One more thing, will this burn the image so that the SD card is bootable?

---

### Post by Cheesemill on 2013-01-12
It could take a while depending on the speed of your card reader.

If the .img file is bootable then your SD card will be. The dd command makes an exact copy in the same way that Win32DiskImager does.

---

### Post by jfever311 on 2013-01-12
So, I need to chill out and get some supper then I guess. What will happen terminal wise when it is finished? 

Cheesemill, are familiar at all with what I am trying to do, rooting and flashing and all that? Oh yeah, thank you very much for your help so far.

---

### Post by dabl on 2013-01-12
"Bootability" relates to a couple of things:

- the interface to the card reader -- is it USB?

- the BIOS on the motherboard -- does it support booting USB devices?

- does the BIOS require the "boot" flag be set on bootable partitions?

---

### Post by jfever311 on 2013-01-12
Here is what I have right now in Terminal.
.
.

---

### Post by Cheesemill on 2013-01-12
It's finished.

---

### Post by jfever311 on 2013-01-12
It sure is. My wife now has Google Play, unknown sources enabled (to add non market apps), and OTA updates are set to manual. She is a happy girl, which makes me a happy guy!!

Thanks again for all the help Cheesemill!!

---

