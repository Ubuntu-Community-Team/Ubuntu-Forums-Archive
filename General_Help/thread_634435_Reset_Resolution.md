---
title: "Reset Resolution"
date: 2007-12-07
forum: General Help
---

### Post by kishorebudha on 2007-12-07
Hi. I am a newbie to Linux. Successfully installed Ubuntu. After I set my screen resolution (dell inspiron 6000) to 1280x800 and rebooted I am unable to view anything. Just a brown band!!! How do I reset screen resolution please?

---

### Post by overdrank on 2007-12-07
> **kishorebudha said:**
> Hi. I am a newbie to Linux. Successfully installed Ubuntu. After I set my screen resolution (dell inspiron 6000) to 1280x800 and rebooted I am unable to view anything. Just a brown band!!! How do I reset screen resolution please?

Hi when you reach the login screen use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command startx  or  to reboot ```
sudo reboot
``` Hope this helps and good luck!

---

### Post by kishorebudha on 2007-12-07
Thank you. That solved my problem.

---

