---
title: "Android connectivity"
date: 2013-04-21
forum: General Help
---

### Post by petersonlevi88 on 2013-04-21
I currently have Ubuntu 32 bit 12.04. I want to connect my LG Motion MS770 Android so I can transfer files such as movies, music and pics. I cannot get the system to see it. I have tried wammu, gammu and abootimg. I have the latest updates. I have tried many different OS's and have only found 2 that see my phone. Zorin and Fuduntu. Fuduntu is a dead horse now Zorin gives me freezing issues, so I want get Ubuntu to work on it. Thanks in advance if anybody can help.

P.S. when I run the gMobileMedia (Mobile Media Browser) it says that I need to connect phone first, which it is and run the setup wizard. I couldn't see any option for a wizard. I'm not sure if I have to manually put settings in on preferences either, as I have no clue which ones they would be.   :D

---

### Post by philinux on 2013-04-21
Try installing gmtp from software centre synaptic or terminal.

---

### Post by scbingham on 2013-04-22
When I wish to transfer files between my Android phone & Ubuntu 12.04 LTS laptop, I use usb & choose the 'set as disk drive' setting. Then move files at will.

Maybe you're trying to achieve something more extravagant.

---

### Post by 3rdalbum on 2013-04-22
That phone runs Android 4, which uses MTP for connecting to the computer. The version of MTP in Ubuntu 12.04 and 12.10 is broken and can't communicate with Android devices.

Your choices are to upgrade to 13.04 or start an FTP server on the phone and connect the phone to Wifi. You can then browse the phone through any FTP client on the computer. (Nautilus works as an FTP client too).

---

### Post by philinux on 2013-04-22
I found the link on my smart phone.

[http://news.softpedia.com/news/How-to-Transfer-Files-from-Ubuntu-to-Android-341722.shtml](http://news.softpedia.com/news/How-to-Transfer-Files-from-Ubuntu-to-Android-341722.shtml)

---

### Post by scbingham on 2013-04-22
I tried gmtp with my Android v 2.2.1 (Froyo), I set usb to charge & data ie set to disk drive.
Nautilus auto started, which I closed, Gmtp complained "Detect: No raw devices found".
It made no difference whether I ejected file system from Nautilus or not.
Is gmtp only for Android v4 & above? Which would be a pity as it looks quite usable.

---

