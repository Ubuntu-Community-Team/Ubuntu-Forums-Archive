---
title: "Cannot get ubuntu 14 to recognise Android phone?"
date: 2014-07-16
forum: General Help
---

### Post by humanracer on 2014-07-16
I tried lsusb and it says
humanracer@humanracer-Compaq-Mini-110c-1100:~$ lsusb
Bus 001 Device 002: ID 058f:3831 Alcor Micro Corp. 
Bus 001 Device 053: ID 22b8:2e83 Motorola PCS 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



my phone is a motorola G. I cannot find the file folder on my desktop. I want to transfer mp3 files to my phone. Can this be done on ubuntu or shall I use my girlfriend's windows computer?

Thanks

---

### Post by ubudog on 2014-07-16
Do you have to "enable USB storage" or something similar on the Android phone?

---

### Post by lisati on 2014-07-16
When I've conncected Android devices via USB, the device usually has a popup asking if I want to turn USB on. Does your phone do this? If so, have you turned USB on?

---

### Post by humanracer on 2014-07-16
No it doesn't say anything like that. I have looked in the phone settings and cannot find anything.

---

### Post by noel6 on 2014-07-16
I use gMobileMedia from the software centre for mine. Picks up phone and does whatever you want. Worth a try with yours.

---

### Post by mooreted on 2014-07-16
Ok, on my Lg G2 with Android 4.4.2 I plug the phone into a USB port. A window pops up on the phone's screen that says, "Select USB connection". The choices are:

Charge Phone
Media Sync (MTP)
LG Software
Send Images (PTP)

To copy files to my phone I select "Media Sync (MTP)".

If you don't see that window, you should see a USB icon in the notification area at the top of your phone's screen. Pull down from the top of the screen to show your notifications and select the USB icon that says, "USB Connected" which will open the window I mentioned above.

---

### Post by 3rdalbum on 2014-07-16
I have a Moto G like you, and Ubuntu 14.04.

When I plug the phone in it displays a quick notification about "Media Transfer Active" or something like that. Then the phone appears at the bottom of the Ubuntu launcher.

If none of this happens, try plugging the phone into a different port directly on your computer.

---

### Post by travis-falkenberg on 2014-07-17
You may have to enable usb debugging on your phone. Its under developer options which is hidden on recent versions of android.

A quick internet search for "enable usb debugging moto g" shows a number of sites with instructions.

---

### Post by coldraven on 2014-07-17
I have a Moto G and I too was puzzled by it not appearing in Nautilus. The answer is to go to Settings then Storage and select the Storage settings (the three dots in the top right corner). Then "USB connection" and choose "Camera(PTP)" instead of "Media Device (MTP)". Hope this helps.

Edit: To clarify, I mean the Settings on the phone not your PC

---

