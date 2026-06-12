---
title: "changing serial port permissions permanently"
date: 2015-09-04
forum: General Help
---

### Post by nathanhurley on 2015-09-04
Hi. I use the USB serial port to connect to routers, but everytime it reboots I have to change permission for /dev/ttyUSB0 and /dev/ttyS0. 

How can I change this permanently so it has chmod 777 on reboot?

---

### Post by SeijiSensei on 2015-09-04
Add the command to the file /etc/rc.local, a script that runs after everything else that starts at boot.  rc.local runs with root privileges, so you don't need sudo, just:
```
chmod 777 /dev/ttyS0
chmod 777 /dev/tty/USB0

```

---

### Post by steeldriver on 2015-09-04
Have you tried adding your user to the dialout group instead? it is sometimes sufficient for serial device connections

---

