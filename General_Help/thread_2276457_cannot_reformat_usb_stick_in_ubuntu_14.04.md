---
title: "cannot reformat usb stick in ubuntu 14.04"
date: 2015-05-02
forum: General Help
---

### Post by cabz on 2015-05-02
I have been having an issue with reformatting / erasing my 8 gig usb stick, I have tried the disk utility in ubuntu and also gparted. neither seem to work. I can delete titles/movies but it doesn't free up the space on the drive.


also in what might be an unrelated issue , when I copy a movie from my desktop to the usb stick it copies just fine and works on the stick and the PC . when I plug the stick into the tv to watch on a larger scale the time of the movie under reports?
the movie might be an hour and a half long but on the tv it only shows the movie as about 40 minutes long? 

if I do the copying in windows everything works as it should everywhere. Since I am trying to do away with windows this is really hanging me up

BTW I am running ubuntu 14.04 dual booted  on my dell laptop if that helps.

---

### Post by sudodus on 2015-05-02
I would wipe the USB stick - start with wiping the first megabyte, and try after that use ***gparted*** to create a new partition table and a partition. The file systems FAT32 and NTFS work will Windows, so I would recommend them for usage in both Windows and linux.

If you have still problems, your stick might improve if you wipe the whole device, and after that try again with gparted.

Use ***mkusb*** to wipe the USB stick

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device](https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device)

See also the following links for more details about pendrives.

[Pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by sammiev on 2015-05-02
> **sudodus said:**
> I would wipe the USB stick - start with wiping the first megabyte, and try after that use ***gparted*** to create a new partition table and a partition. The file systems FAT32 and NTFS work will Windows, so I would recommend them for usage in both Windows and linux.

If you have still problems, your stick might improve if you wipe the whole device, and after that try again with gparted.

Use ***mkusb*** to wipe the USB stick

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device](https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device)

See also the following links for more details about pendrives.

[Pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I have been using ***mkusb*** for sometime now and it has been great on my USBs. +1

---

