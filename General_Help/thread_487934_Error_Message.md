---
title: "Error Message"
date: 2007-06-29
forum: General Help
---

### Post by cjblade54 on 2007-06-29
I just installed the new Ubuntu.  Everytime I tunred on the machine, this message appears:
Internal Error
Failed to initialize HAL!

It seems like everything else is working.  Need help to get rid of that message.  Thank you.

---

### Post by misconfiguration on 2007-06-29
Is your CDROM/DVD working? Generally this is a specific issue with your object-oriented media devices. Check to see if you can use it, if you can't I would try to upgrade firmware for this device, if that doesn't work maybe consider replacing it?

---

### Post by cjblade54 on 2007-07-02
You were right... I don't think both my CD and DVD are working.  How do I update the driver for these devices?

---

### Post by khedron on 2007-07-02
What model numbers are they?

---

### Post by cjblade54 on 2007-07-02
hp dvd writer dvd200i and Compact dsik DVD ROM

---

### Post by khedron on 2007-07-02
The problem with updating firmware is that the hardware manufacturers often provide Windows-only programs. This seems to be the case here.

A search on HP.com gives [this page]("http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&cc=us&dlc=en&product=81681&lang=en"); the firmware updater is Windows-only. If you have a Windows partition you can run it from there; if not then I'm afraid you're out of luck.


Did your DVD drive actually work with Windows before you installed Ubuntu?

---

### Post by cjblade54 on 2007-07-03
Yeah... they both work in Windows environment.  I have doul boot with XP and Ubuntu on the same box.  It works with XP but not Ubuntu.

---

### Post by khedron on 2007-07-03
Could you possibly post the output of this command:
```
sudo dmesg
```
You can put the output into a file /dmesg-output by doing this instead:
```
sudo dmesg >/dmesg-output
```

---

