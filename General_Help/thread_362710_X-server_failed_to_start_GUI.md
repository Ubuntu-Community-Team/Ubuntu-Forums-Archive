---
title: "X-server failed to start GUI"
date: 2007-02-15
forum: General Help
---

### Post by d-train24 on 2007-02-15
i am getting a x-server error it says that it has failed to start my GUI and moves me to the command line i have reinstalled, updated, opend and investagated the xorg file but once you configure how are you supposed to test it, other than reboot by the way this cd is a requested free cd sent by mail????

---

### Post by dcstar on 2007-02-15
> **d-train24 said:**
> i am getting a x-server error it says that it has failed to start my GUI and moves me to the command line i have reinstalled, updated, opend and investagated the xorg file but once you configure how are you supposed to test it, other than reboot by the way this cd is a requested free cd sent by mail????

Many answers in this forum are available with a simple search, your answer would be:
```
sudo /etc/init.d/gdm restart
```
after any changes to the xorg.conf file.

If it doesn't work, then do this and select the VESA driver:
```
sudo dpkg-reconfigure xserver-xorg
```

That should get you a basic X system running and then you can begin to investigate getting the correct driver for your hardware working.

---

### Post by d-train24 on 2007-02-16
figured it out i had the reconfigure cmd but i was confused how to restart apparently there is a cmd that restarts the x server that is called startX it restarted and loaded perfectly. thanks for the help. :guitar:

---

