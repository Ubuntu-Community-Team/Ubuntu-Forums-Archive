---
title: "Nokia 6131 connectivity"
date: 2006-10-28
forum: General Help
---

### Post by Zalbor on 2006-10-28
I have this phone, and I was wondering what the best way to connect it to my PC is. I have two options:
1)Buy a bluetooth device for my PC.
Upside: It will work with Ubuntu.
Downside: It's slow!
2)Buy a USB cable for my phone
Upside: It's fast
Downside: I'll have to use Windows to transfer files.

I'm not basically asking for opinions (although they're welcome) but for whether it's possible to transfer files through Ubuntu, using a USB cable. Synchronization etc don't interest me...

---

### Post by louis_nichols on 2006-11-01
I have the same phone and same questions. :)

I was just googling around and saw that 6131 and USB should work under Linux, for file transfer. I haven't discovered the exact way to do it, nor do I have a USB cable, to test it. On the other hand, I strongly consider bying a Bluetooth dongle. I don't know about the difference in speed, but I am willing to trade that off for the extra versatility offered by Bluetooth.

A more interesting issue I'm thinking of is to what extent would it be possible to use the device as a modem via bluetooth... or USB, for that matter.

---

### Post by ingo on 2008-01-25
Have any of you made any progress? I need to get it working with bluetooth but cannot get it to connect!

Cheers

---

### Post by louis_nichols on 2008-01-25
It's been a while and I have since given up and started connecting the phone to my wife's laptop, where she uses XP.

But I seem to remember that I was able to download the phone book. No more than that.

---

### Post by matthewcraig on 2008-01-25
Why not use a cheap bluetooth adapter?  Works great with Ubuntu.

---

### Post by Alex_Perry on 2008-01-27
I'm currently using a 6131 and I am able to share files via bluetooth. I am, however, using KDE and it's bluetooth service, kbluetooth.

---

### Post by ingo on 2008-01-27
yep, got it connected on bluetooth and would like to use kitchensync now to automatically sync kalender and addresses but haven't made any progress. 

The reason why it didn't work before was because I was using a pre-Neanderthal bluetooth stick...

---

### Post by plenque on 2008-01-27
I'm using bluetooth and it works as expected.
I was having a problems with the USB connection (it seemed to reject big transfers) but I resolved it following this suggestion: 
[http://www.mail-archive.com/linux-usb-devel@lists.sourceforge.net/msg46994.html](http://www.mail-archive.com/linux-usb-devel@lists.sourceforge.net/msg46994.html)

By the way, at the kernel changelog it says it should work with version 2.6.23. It was corrected before (on 2.6.19 I think) but for an old version of the firmware.

---

### Post by Frants on 2008-02-08
Yep, thanks to the latest link in this thread my 6131 works quite well in Ubuntu. I have to change in /sys/block/sda/device/max_sectors to 64 instead of 240 everytime I want to transfer something, but it's working :) I'm running 2.6.22-14 kernel and the firmware 5.50 on the phone.

---

