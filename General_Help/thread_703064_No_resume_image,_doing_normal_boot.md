---
title: "No resume image, doing normal boot"
date: 2008-02-20
forum: General Help
---

### Post by thomeboy on 2008-02-20
I was playing Regnum Online, when i got disconnected and my computer seemed to freeze. So i hit alt+ctrl+f1 and did a reboot.

After it rebooted, my monitor says Video Mode Not Supported and then goes to command line and says

kinit: no resume image, doing normal boot...

then after a minute or so it just goes to the command line and I can't go over to f7. 

this is killing me as my computer now is not usable. I tried running sudo dpkg-reconfigure xserver-xorg and then i select default options, but that doesn't do anything.

I need help, I don't want to restore my computer back to windows.

---

### Post by Carl H on 2008-02-21
What graphics card do you have? Are you using the Linux drivers or the proprietary ones?

---

### Post by torro on 2008-02-22
Sorry do not have a solution, but are experiencing the same problem. The problem started after connecting the computer to an external projector, and are getting the following additional information:

kinit: name_to_dev_t(/dev/disk/by_uuid/....... = sda4(8,4)
kinit: trying to resume from /dev/disk/.....
kinit: no resume image, doing normal boot .....

I am using an AMD64 installation on an ACER Aspire Laptop.

Suspect the graphical drivers has been messed up, but are a novice in using LINUX - but has been very satisfied after switching from Windows, and has the same desire not to recover in Windows Vista.

Hope for some help.

---

### Post by torro on 2008-02-24
Found a solution that worked for me posted by dstew under the question "boot trouble"

Basically entered 
```
sudo dpkg-reconfigure xserver-xorg
```

and after the reconfiguration restarted the xserver with
```
Startx
```

---

