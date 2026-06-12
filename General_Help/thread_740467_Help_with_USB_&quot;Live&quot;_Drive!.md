---
title: "Help with USB &quot;Live&quot; Drive!"
date: 2008-03-30
forum: General Help
---

### Post by kurt1288 on 2008-03-30
I'm trying to get my USB drive to work as a bootable drive and as a writable hard drive. I've followed the instructions from [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)
I can boot using the USB just fine. The problem is, is that whenever I try to have something save to the drive, it always is saved to a "filesystem" drive (the name of the drive that is displayed in "Places->Computer" is filesystem). If I got to the partition editor and look at the usb drive, it shows the boot partition and what should be the writable partition (yes, that part is named ("casper-rw"). But it GParted also says that it is unable to find a mountpoint for the 2nd partition. What do I do so that I can have stuff save to the USB drive? Thanks.

---

### Post by dmitriyp13 on 2008-03-31
I haven't used a live USB drive before, but it sounds like you can just use GParted to set the mount point of the second partition to something like /media/usb and write files there.

---

### Post by dixonh2 on 2008-03-31
To: Kurt1288

I'm trying to gain information to make an external USB HDD bootable with Feisty.

The information provided by your link MIGHT be useful. But it's written to make a thumb drive bootable. But thumb drives ( or pen drives ) are solid state devices , not discs like wht I have. 

[http://www.pendrivelinux.com/2007/09...ibbon-install/](http://www.pendrivelinux.com/2007/09...ibbon-install/)

Won't the instructions for a solid state device be somewhat different?

Anyway,  I may have bitten off more than I can chew here. I have never been in the Linux world before since I'm a Windows tech. Woe is me!

---

### Post by kurt1288 on 2008-03-31
I'm using Gutsy. I've pretty much given up with the LiveUSB as well as persistence. I've switched to back to the LiveCD and persistent USB, but I am again unable to get that to save anything to the USB.

---

