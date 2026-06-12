---
title: "after upgrade restart, X server fails"
date: 2006-10-27
forum: General Help
---

### Post by cptjaben on 2006-10-27
when my computer restarted at the end of the 6.10 upgrade, upon reloading I get the message X server failed and it tells me to restart GMD when x Server has been reconfigure. and gives me a command prompt. Does anyone know how this might be fixed? Thanks.

---

### Post by mjziegle on 2006-10-27
video card chipset?
printout of /var/log/Xorg.0.log?
exact error message?

---

### Post by bulldog on 2006-10-27
Try```
sudo dpkg-reconfigure -phigh  xserver-xorg
```

---

### Post by cptjaben on 2006-10-27
Thanks for the help, it worked out nicely, just restarted ubuntu after using that command. Thanks again

---

### Post by ~LoKe on 2006-10-27
That's fine.  Give us the log, please.

---

