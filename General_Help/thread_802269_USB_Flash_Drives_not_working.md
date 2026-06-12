---
title: "USB Flash Drives not working"
date: 2008-05-21
forum: General Help
---

### Post by tjb891 on 2008-05-21
I just installed 8.04 and my usb ports will not detect flash drives. They will detect usb wireless cards,usb mice, and usb keyboards. Does anyone have an idea of how I can find out what is wrong with it.

---

### Post by rbc on 2008-05-21
What is happening or not happening? Errors? Can you manually mount it?

---

### Post by cdtech on 2008-05-21
With the card plugged in try "df -H" and see if its listed, if not try "sudo /etc/init.d/hal restart". You should get " * Restarting Hardware abstraction layer hald". Then look at df command again, if nothing, I've heard for this problem with 8.04 is to uninstall "hal" and reinstall.

---

### Post by cubeist on 2008-05-21
Can you post the last few lines of *dmesg* (just type this in a terminal) after inserting your usb drive... this will show what is being recognized, if anything.

---

