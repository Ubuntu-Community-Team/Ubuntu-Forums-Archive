---
title: "Help to read a knackered SD card"
date: 2015-11-03
forum: General Help
---

### Post by trisgti2 on 2015-11-03
hi all,
I'm hoping that someone will be able to help me - I have a microSD card from a S4 phone that contains family photos but I now cannot read or even mount it.

I believe there is hope - popping it into a USB reader shows some signs of life..

```
ls -la /dev/sd*
brw-rw---- 1 root disk 8,  0 Nov  3 20:45 /dev/sda
brw-rw---- 1 root disk 8,  1 Sep 17 11:55 /dev/sda1
brw-rw---- 1 root disk 8,  2 Sep 17 11:55 /dev/sda2
brw-rw---- 1 root disk 8,  3 Sep 17 11:55 /dev/sda3
brw-rw---- 1 root disk 8, 16 Nov  3 21:10 /dev/sdb <-- microSD card

```

but.. where do I go from here?

any help would be very gratefully received.

---

### Post by SuperFreak on 2015-11-03
You could try TestDisk it is in Software Center ,Photorec may be able to recover your pictures it is run through command line once you install Test Disk

```
sudo photorec
```
follow the terminal instructions

---

### Post by trisgti2 on 2015-11-04
> **SuperFreak said:**
> You could try TestDisk it is in Software Center ,Photorec may be able to recover your pictures it is run through command line once you install Test Disk

```
sudo photorec
```
follow the terminal instructions

thanks for the suggestion, but photorec cannot see the microSD card :(
```

PhotoRec 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

  PhotoRec is free software, and
comes with ABSOLUTELY NO WARRANTY.

Select a media (use Arrow keys, then press Enter):
>Disk /dev/sda - 320 GB / 298 GiB (RO) - Hitachi HTS543232L9A300



>[Proceed ]  [  Quit  ]

Note:
Disk capacity must be correctly detected for a successful recovery.
If a disk listed above has incorrect size, check HD jumper settings, BIOS
detection, and install the latest OS patches and disk drivers.


```

---

### Post by Bucky Ball on 2015-11-04
Could you run:

```
sudo blkid
```

... with the SD card in, please, and post the output back here?

---

### Post by trisgti2 on 2015-11-04
here's the output.. no mention of sdb :s

```
sudo blkid
/dev/sda1: UUID="5f42ed52-1efe-4a4f-b493-ba795b59e7f9" TYPE="ext3" 
/dev/sda2: UUID="c4d94314-74f7-4d7d-826d-b46e49cd4a01" TYPE="swap" 
/dev/sda3: UUID="90ade97b-8aee-464f-9183-4585d094e6f3" TYPE="ext3"
```

---

### Post by trisgti2 on 2015-11-06
any further ideas anyone..?

---

### Post by QDR06VV9 on 2015-11-06
> **SuperFreak said:**
> You could try TestDisk it is in Software Center ,Photorec may be able to recover your pictures it is run through command line once you install Test Disk

```
sudo photorec
```
follow the terminal instructions
+1 

PhotoRec, Has been a life saver for me, from bad cd's dvd's usb drives, and yes memory cards(sim's).
You will need a card reader that will pulg in to your computer though.
The method I use is on a USB drive, I purchased PartedMagic then burned it to the thumb drive,Then I boot to the partedmagic.
Went to menu and selected QPhotoRec GUI and from there it was pretty straight forward.
Be sure to plug the card you are trying to rescue from in. 
Your card should show up with this method, It has for me 100% of the times used.
Just mentioning it if nothing better comes up.


[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)


[http://partedmagic.com/downloads/](http://partedmagic.com/downloads/)

**EDIT: **[Create a TestDisk FreeDos LiveCD]("http://www.cgsecurity.org/wiki/Create_a_TestDisk_FreeDos_LiveCD")
I have not used this one. But it was free.
Best of Luck
Regards

---

### Post by SuperFreak on 2015-11-11
[http://www.howtogeek.com/232931/how-to-recover-images-off-a-corrupted-sd-card/](http://www.howtogeek.com/232931/how-to-recover-images-off-a-corrupted-sd-card/)

---

