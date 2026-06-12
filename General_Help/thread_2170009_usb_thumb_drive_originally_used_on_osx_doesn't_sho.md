---
title: "usb thumb drive originally used on osx doesn't show up when plugged into ubuntu pc"
date: 2013-08-24
forum: General Help
---

### Post by msousa on 2013-08-24
Hi

I have a thumb drive that I originally used with an imac but now I want to use it with my ubuntu 12.04 laptop. It shows it's empty in osx but when I plug it into my laptop it doens't show up anywhere I've looked. I tried "sudo fdisk -l" and "dmesg | grep tty" and have looked into /media but it doesn't show up anywhere. Any idea what I need to do to use the thumb drive in my ubunto machine?

Thanks...

Mike

---

### Post by VMC on 2013-08-24
tail syslog then plug in your device and watch/wait for messages

```
tail -f /var/log/syslog
```

---

### Post by msousa on 2013-08-24
VMX, thanks for the info. The USB drive became usable once I did a reboot of my laptop -- not sure why, but this seemed to fix it.

---

