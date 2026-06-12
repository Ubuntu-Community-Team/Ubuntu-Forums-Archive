---
title: "Ubuntu 7.1 cannot chage resolution"
date: 2007-12-23
forum: General Help
---

### Post by kasun04 on 2007-12-23
On my Ubuntu 7.1 installation, I chaged the screen resolution by going to  admin>screen n graphics
and chage resolution to 1280x1024 and it was supported by my monitor and ask for keep config and it works fine till i logged off. Once I logged in again the resolution is restored back to the old one(which is not 1280 * 1024)

---

### Post by jken146 on 2007-12-23
Press Ctrl+Alt+F1.  Log in.  Then run these commands: ```
sudo /etc/init.d/gdm stop

sudo dpkg-reconfigure xserver-xorg

sudo /etc/init.d/gdm start
```

---

