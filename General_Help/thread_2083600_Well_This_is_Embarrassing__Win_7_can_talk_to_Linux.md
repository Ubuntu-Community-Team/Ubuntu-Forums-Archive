---
title: "Well This is Embarrassing  Win 7 can talk to Linux but Ubuntu Can't"
date: 2012-11-13
forum: General Help
---

### Post by Quarkrad on 2012-11-13
Having migrated my mother-in-law to Linux/Ubuntu a few years ago (running 12.04) she has bought herself a Samsung Galaxy Tab 2 (7.0) and asked me what she can do with it.  My first thing was to port some pictures on it but when you plug it in to a usb port Ubuntu does not 'see it'.  I'm hoping there is something I can do re Ubuntu to make it visible but Win7 sees it 'out of the box'.  There is obviously a good reason for this (90% + of Galaxy Tab users probably have Windows so they have made it visible, I guess a mac can see it as well) but at a 5000ft view I would have thought that at a file manager level Ubuntu Linux would have seen something (Android Linux).  Is there anything (easy) I can do to transfer files to it?

---

### Post by dino99 on 2012-11-13
look at your disk settings; is that one mounted ?

---

### Post by HermanAB on 2012-11-13
$ sudo dmesg
plugitin
$ sudo dmesg

Google...

---

### Post by mastablasta on 2012-11-13
have a look here maybe: [http://ubuntuforums.org/showthread.php?t=2030732](http://ubuntuforums.org/showthread.php?t=2030732)
 
edit: also Android uses a heavilly modified kernel. and only kernel is linux kernel while the rest (various module etc.) is not .

---

### Post by cwsnyder on 2012-11-13
I have a Samsung Galaxy Tab 2 7.0, and it doesn't connect through USB to Windows or Linux for full 2-way drag & drop file management.

You can download from the tablet, but the Samsung app (Kies) does not let you upload to the tablet.  I put on AirDroid (Android app), and the same no go for regular file management, either USB or network WiFi.

You can add a microSD card and access that from an SD card reader on your computer and from your file manager on the tablet and that is the only way I have found to transfer books, magazines, etc. to the tablet for usage.

You might be able to use a special MTP file system and connect via USB or AirDroid, but I haven't got it working.

The 'official Samsung' way is through the cloud [http://www.samsung.com/us/article/how-to-set-up-and-sync-a-galaxy-device](http://www.samsung.com/us/article/how-to-set-up-and-sync-a-galaxy-device) and only works for media files, contact information, calendar, & memos.

---

### Post by Mark Phelps on 2012-11-13
The reason that Win7 can "see" the Galaxy Tab (and other newer Android devices) is that Samsung made drivers for that.  They also provide an app (Kies Air) that comes with drivers.

Neither of these is available in Linux.

Once again, it's a driver problem.

---

### Post by Quarkrad on 2012-11-13
Thanks for your suggestions.  I've just connected the tab to win7 via Virtualbox (on my 12.04 pc) and via explorer copied a photo and music file to the tablet!  Seems to work for some people and not others.  My mother-in-law does not have virtualbox/win7 on her machine - it would be nice if nautilus worked as easily as explorer.

---

### Post by Quarkrad on 2012-11-13
When I plug the tablet in and enter lsusb in the terminal I get this device:

**Bus 002 Device 008: ID 04e8:6860 Samsung Electronics Co., Ltd GT-I9100 Phone [Galaxy S II]**

is there a mount command I can use to access it (newbie talking!)?

---

### Post by dannyboy79 on 2012-11-13
wonder if you would have more success if you rooted it?

---

### Post by philinux on 2012-11-13
I can browse my un rooted galaxy s3 fine from ubuntu. you may need to change the connection type from media to usb.

---

### Post by Quarkrad on 2012-11-13
Afraid I'm a newbie so need a bit of hand holding - how do I change from media to usb?

---

### Post by philinux on 2012-11-13
> **Quarkrad said:**
> Afraid I'm a newbie so need a bit of hand holding - how do I change from media to usb?

Thats on the samsung device on my phone its from the swipe from top dropdown.

You need the manual for your tab.

---

### Post by Quarkrad on 2012-11-13
Doesn't look like I've got that option.

---

### Post by philinux on 2012-11-13
> **Quarkrad said:**
> Doesn't look like I've got that option.

Indeed it should just work as a mass storage device.

> Connecting as a Mass Storage Device
You can connect your device to a PC as a removable disk and
access the file directory. If you insert a memory card in the
device, you can also access the files directory from the
memory card by using the device as a memory card reader.
Note: The file directory of the memory card displays as folder
Card, separate from the internal memory, which is folder
Tablet.
1. Insert a memory card into the device to transfer files
from or to the memory card.
2. Attach your device to the computer with the USB cable.
Your computer recognizes the connection and displays
the AutoPlay screen.
143
3. Click the option to Open device to view files.
You should see a Card and a Tablet folder.
4. Copy files from the PC to the memory card (Card
folder).
5. When finished, close the PC folder and disconnect the
USB cable.

---

### Post by patrick-epl15 on 2012-11-13
I don't have a tablet.  Do you get a list of options when connecting to a pc (charge only, etc....)?

---

### Post by cwsnyder on 2012-11-13
I checked out the Filezilla on Linux, Rapfox FTPServer app on Android, and it works a treat!  About 2MB/sec file transfer rate on my 802.11n router.

I couldn't get it to work with SSH, but the Rapfox app, just called FTP Server in the Google Play Store, worked just fine with the settings given for bi-directional file transfer.

---

### Post by Quarkrad on 2012-11-13
Thanks - it looks like either FTP or a micro sd card is the way to go.

---

