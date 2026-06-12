---
title: "Help with Udev / MTP / Android Fastboot"
date: 2016-09-21
forum: General Help
---

### Post by gde061-www on 2016-09-21
I'm having some trouble mounting a USB device in 14.04.  Specifically a Kindle Fire in *_Fastboot_* mode.

I have tried the tutorial on this site for mounting with MTP.  I've done the lsusb command, made the associated changes in the /etc/udeb/rules.d and /lib/udev/rules.d, although frankly I don't understand what they are doing.  I just understand that this device tries to mount with MTP when I connect it, but really what I want is for it to mount in file transfer mode instead.  

When the device is not in Fastboot, it mounts fine, and I can issue adb commands to it and everything.  In fastboot, I get an error in Nautilus: **Unable to access “Tate PVT 08” / Unable to open MTP device '[usb:001,006]'**

I would appreciate not just specific information on how to possibly resolve this specific problem, but also links to information that would explain thoroughly the process Ubuntu is using to mount USB devices (i.e., as MTP device vs. file transfer mode), what the various config files do, and how to control them with rules in the config files.  

As I understand it, this is a common problem and in Windows there is a simple fix where you change the associated device driver in the Device Manager.  How do you do something similar in linux, so that it won't try to use the MTP protocol to communicate with the device but instead will use the correct driver for a Kindle Fire in fastboot mode?

Thanks

---

