---
title: "failed to initialize HAL! ?"
date: 2006-11-12
forum: General Help
---

### Post by thewatts on 2006-11-12
so i installed automatix and with it installed some applications.  restarted my computer and everything was fine -- shut it down and left for a couple hours.


come back, turn it on -- and get this error:

Internal Error:
Failed to Initialize HAL!



What is HAL? and how can I fix it?

`thanks

---

### Post by El Menda on 2006-11-16
Hi man. Search in forums. There are a lot of people like u... and me. I have the same problem but im looking for solutions.
Bye!

---

### Post by loell on 2006-11-16
HAL is an acronym (Hardware abstraction layer)

hal allows easy userspace device management with UDev and D-BUS.
if there is hal error, mostly you can't access your usb devices

you can restart hal by 

 sudo /etc/init.d/dbus-1 restart

---

### Post by code_monkey on 2006-12-08
Hi, I had same problem but fixed it like loell said but instead of "sudo /etc/init.d/dbus-1 restart" what worked for me was sudo /etc/init.d/dbus restart . just dont ad the quotes ha,ha then reboot. hope that helps .

---

