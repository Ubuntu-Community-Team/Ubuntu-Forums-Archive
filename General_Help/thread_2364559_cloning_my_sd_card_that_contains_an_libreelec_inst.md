---
title: "cloning my sd card that contains an libreelec installation, is there a tool for that?"
date: 2017-06-24
forum: General Help
---

### Post by ronjjjg8885 on 2017-06-24
in windows there is a tool.
i'm asking for a tool because i'm not familiar with how to locate where the card is mounted at.

if there is not such a tool. please tell me where to find the right explanations for how to figure the card location.

---

### Post by howefield on 2017-06-24
I'd recommend Clonezilla for that.

There is a learning curve but to be honest using the default settings and going through the "wizard" should get you there. But perhaps you don't feel up to that ?

---

### Post by ronjjjg8885 on 2017-06-24
thanks
i wanted to try clonezilla now after you mentioned it but i see that it isn't included in the aptitude library.
why is that?

---

### Post by howefield on 2017-06-24
You would have to download Clonezilla from [http://clonezilla.org/downloads.php](http://clonezilla.org/downloads.php)

Then create a boot up media - either on a CD or a USB stick, eg to create a bootable USB stick...

1. Download Clonezilla zip file.
2. Unzip and extract all files to the USB drive.
3. Navigate in terminal to the /utils/linux/ folder on the USB stick.
4. Run the command (where xN is disk/partition) : sudo bash makeboot.sh /dev/sdxN 

Be very sure that you have the correct device before running the makeboot.sh file.

Or of course use a CD and make the bootable media with brasero or xfburn, ect.

---

### Post by ronjjjg8885 on 2017-07-01
thanks

---

### Post by C.S.Cameron on 2017-07-01
In Linux the traditional tool to clone a drive is dd.
Use Disks to confirm the drive you wish to clone (sdx), and the target (sdy)
In terminal run:
```
dd if=/dev/sdx of=/dev/sdy
```
Cloning may take some time.
If you have any doubts use clonezilla, with dd small errors can go a long way.

Edit:
Not sure about Libre but OpenELEC has a builtin backup tool that will "Create System and Kodi Backup"
It is probably good enough for the average user.
However if you want to mass produce Kodi boxes it might be best to use dd to create an .img file of the drive.
```
dd if=/dev/sdx of=/image.img
``` ,(if I recall correctly).
You can then use dd, mkusb, (or Imagewriter in Windows), to write the bootable disk image direct to USB.

---

