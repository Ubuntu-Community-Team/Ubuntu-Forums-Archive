---
title: "question about mounting android"
date: 2014-04-06
forum: General Help
---

### Post by charitosha on 2014-04-06
Is it possible to mount an android device if its IDs are known? 
i am asking because even if usb debuging is off i don't see it anywhere (no folders or anything).. 
i see that the device is connected only by some commands e.g. lsusb 
even if i do it through adb devices it is shown.
but how to mount something if you don't have a folder to mount to??? :confused:

---

### Post by mcduck on 2014-04-07
What Android device it is, and which Android version it is running? Later Android versions so not operate as removable drives any more, but instead use the MTP protocol to give you access to their files. Ubuntu versions from 13.04 forward should support MTP devices by default, and also some devices might have option to switch between disk mode and MTP mode.

---

### Post by efflandt on 2014-04-08
For example Samsung S3 (currently Android 4.3) USB is MTP (media mode) by default or can be switched to PTP (photo mode). In 12.04 nautilus only shows root directories in phone storage and microSD (nothing in those directories). In PTP mode nautilus shows everything in phone storage, but nothing at all for microSD. Nothing I have tried with mtpfs, etc. has worked to do anything else, so I use sftp (AndFTP for sftp client on phone, or SSHServer for sftp from Linux).

In 13.10 nautilus can see everything on the phone in MTP mode, and files can be copied from the phone, but files cannot be opened on the phone (they need to be copied to Linux first).

---

