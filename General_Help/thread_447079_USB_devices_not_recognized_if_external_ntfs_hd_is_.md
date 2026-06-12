---
title: "USB devices not recognized if external ntfs hd is off"
date: 2007-05-17
forum: General Help
---

### Post by pete222 on 2007-05-17
Interesting problem- I have feisty, XP dual boot separate hd system with an external HD for backups (esata). I also have a yepp mp3 player and a usb thumb drive that I like to connect in feisty but if I dont have my external esata hd turned on (ntfs and and ext3 just for backups) none of these devices are recognized- 

when the external HD is on I can "hot plug" any usb devices and they are immediately recognized. But if the HD is off nothing gets recognized even if I boot the PC with the devices plugged in (I can see them in the bios boot screen). 

Also I have the NTFS config tool installed. 

any advice?

---

### Post by spamking2000 on 2007-05-17
That is strange. One work around, you could define the usb drives in fstab so that your system always sees them. Google fstab and you should see some examples of how to set that up. You'll have to do it as the superuser, so sudo gedit /etc/fstab to get into the file.

---

