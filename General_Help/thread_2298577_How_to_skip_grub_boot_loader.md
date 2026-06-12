---
title: "How to skip grub boot loader?"
date: 2015-10-12
forum: General Help
---

### Post by nathan84 on 2015-10-12
Originally in my installation the grub boot loader was skipped. Ever since I did something yesterday, however it is not. What happened was I was doing something and had to do compiz --reset and decided to close the terminal so I had to restart since I couldn't type anything, I had to use the button and do a hard shutdown on the PC. When it booted it booted to the grub boot loader, which prompted me to press enter before I went into Ubuntu and now it has done the same thing ever since.

---

### Post by leclerc65 on 2015-10-12
Edit /etc/default/grub
and change line GRUB_TIMEOUT to 0.
The do a 
```
 sudo update-grub
```
I would change it to 2 or 3. I'd rather wait 2, 3 seconds to have ability to choose other options (Recovery for ex.) when needed.

---

### Post by pfeiffep on 2015-10-12
> **leclerc65 said:**
> Edit /etc/default/grub
and change line GRUB_TIMEOUT to 0.
I would change it to 2 or 3. I'd rather wait 2, 3 seconds to have ability to choose other options (Recovery for ex.) when needed.
I think that after editing this file one needs to execute ```
sudo update-grub
```

---

### Post by leclerc65 on 2015-10-12
Sorry pfeiffep .
I edited my post while you were posting.

---

### Post by Bucky Ball on 2015-10-12
You can set it to '0' and if you want to see the menu at boot I think hitting shift will bring it up (from memory). You don't need to set it to 2 or 3 seconds.

---

### Post by nathan84 on 2015-10-12
It seems the problem fixed itself after another two reboots...

---

### Post by Bucky Ball on 2015-10-12
Please see the first link in my signature. Enjoy. :)

---

### Post by Hodor on 2015-11-18
I've tried the suggestions in this forum, no joy.

At /etc/default/grub I have
```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbcore.autosuspend=-1"
GRUB_CMDLINE_LINUX=""
```

after updating I ran  sudo update-grub and rebooted (a few times for good measure) - still the grub menu

I have a dual boot setup but only ever boot into ubuntu from the grub menu.
Is there an alternative configuration file that sometimes gets used?

---

### Post by Hodor on 2015-11-19
I'm going to start a new thread for this, since its a different query to the op.

---

