---
title: "LDAP Users USB Devices and Audio"
date: 2007-08-28
forum: General Help
---

### Post by lucsmath on 2007-08-28
Hello,

I have a situation where the majority of my users log in via LDAP and have their home directories automount from an NFS server.  These things are working correctly however since ubutnu is so group permission heavy things like audio and usb automounting are a problem.

I got the audio working by adding MODE="0666" to the audio section of the udev permissions file but I have not found a fix for the usb automount problem.  I've crawled through various posts but have not found a solution.  Does anyone know how to get usb automounting working for LDAP users?

---

### Post by Tobbera on 2007-09-11
Please see [http://ubuntuforums.org/showthread.php?p=3347625&posted=1#post3347625]("http://ubuntuforums.org/showthread.php?p=3347625&posted=1#post3347625")

---

