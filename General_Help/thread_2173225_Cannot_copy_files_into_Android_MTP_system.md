---
title: "Cannot copy files into Android MTP system"
date: 2013-09-08
forum: General Help
---

### Post by Raphael_Rocha_da_Silva on 2013-09-08
Hello! 


I'm experiencing this trouble: for some reason, I cannot copy files into a tablet device. 


When I try to copy a folder from my computer to the tablet device, the transferency freezes at 12kB. The same happens when I try to copy from the device to my computer, vice-versa.


When I try to copy a folder from the device to itself, I get the error: "**Error copying file to mtp://[usb:002,009]/Tablet. Operation not supported.**"


I can rename the folders that are in the device, though. 


I've already tried to run "**sudo add-apt-repository ppa:langdalepl/gvfs-mtp**" and update and upgrade, which took no effect.


I am using Ubuntu 12.04 on my computer, and the tablet runs Android 4.1.1.


I hope somebody is able to help me. 


Thanks.

---

### Post by MartyBuntu on 2013-09-08
For "drag and drop" or copy/paste, you should be using **MSC**...

---

### Post by SeijiSensei on 2013-09-08
Support for MTP was pretty poor before 13.04.  I upgraded to that version just so I could have Ubuntu talk to my Galaxy S3 with Android 4.1.2.  Overall I'd rather run an LTS version like 12.04, but the absence of solid MTP support forced me to adopt a different policy.

The best solution for 12.04 I found was to spend $3 and install [Wifi File Transfer Pro]("https://play.google.com/store/apps/details?id=com.smarterdroid.wififiletransferpro&hl=en") which lets you exchange files with the device using a browser.

---

### Post by carlwsnyder on 2013-09-08
+1 for SeijiSensei.  Any Android device after ICS does not really support file transfer through USB except for music, pictures, and other recognized data types using the MTP (media transfer protocol) drivers.  See the following article for instructions through 13.04: [http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html](http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html)

Anything else, I have been using Filezilla on my desktop and Rapfox FTP server [https://play.google.com/store/apps/details?id=com.rapfox.ftpsvr&hl=en](https://play.google.com/store/apps/details?id=com.rapfox.ftpsvr&hl=en) over wireless.

---

### Post by Suragch on 2014-04-08
I discovered a quick workaround was to rename my file with an .mp3 extension. I was then able to transfer my file. Then I could rename it back to the original name and use it again.

---

### Post by Eric_Atwood on 2014-04-08
I've been using gMTP on my 12.04 desktop to move files to/from my devices for some time.  It's not particularly fast, but it has some (limited) drag-and-drop support and has worked well with every device I've tried.  This list includes NOOK HD, Kindle Fire, HP 7" tablet, iPhone 4, iPhone 5, Moto X, and a handful of Samsungs.

---

