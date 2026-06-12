---
title: "prevent automount of external drive"
date: 2012-11-03
forum: General Help
---

### Post by jsvidyad on 2012-11-03
Hello,

   I use kubuntu 10.04. The usual behavior of the system when an USB external drive(external hard drive or flash drive) is plugged in via USB is to automatically mount it and then open the file browser showing the contents of that external drive. Now, I'd like to prevent this from happening. I do not want any such USB external drive(external hard drive or flash drive) to be mounted automatically. In fact, I don't even want the system to attempt to automount such an USB external drive(external hard drive or flash drive). I know that in ubuntu this can be done via gconf-editor. But, I don't know how to do the same in kubuntu. Can someone please help me with this? Again, I'm using kubuntu 10.04.

  Thank you in advance.

---

### Post by jsvidyad on 2012-11-04
Can someone please help me with this?

---

### Post by jsvidyad on 2012-11-06
Can someone please help me with this?

---

### Post by drmrgd on 2012-11-07
I'm not sure about 10.04, or more precisely the KDE version that you currently have (if not the latest).  One way to do it, though, is to check under System Settings -> Removable Devices.  There you should see some automounting options for removable devices, and I believe you can change it so that the device is recognized, but not automatically mounted.

---

### Post by jsvidyad on 2012-11-07
Thanks for your help

---

### Post by rnerwein on 2012-11-08
> **jsvidyad said:**
> Hello,

   I use kubuntu 10.04. The usual behavior of the system when an USB external drive(external hard drive or flash drive) is plugged in via USB is to automatically mount it and then open the file browser showing the contents of that external drive. Now, I'd like to prevent this from happening. I do not want any such USB external drive(external hard drive or flash drive) to be mounted automatically. In fact, I don't even want the system to attempt to automount such an USB external drive(external hard drive or flash drive). I know that in ubuntu this can be done via gconf-editor. But, I don't know how to do the same in kubuntu. Can someone please help me with this? Again, I'm using kubuntu 10.04.

  Thank you in advance.

hi
i had the same problem and modified my /etc/fstab
the /dev/sdf i an external usb:

i insert: /dev/sdf1 /koala_root       ext2 defaults,suid,[COLOR=Blue]noauto[/COLOR]  0 0
this prevents the OS to mount the device under /media/.....
if i want to work with that device just type ( as root)
mount /koala_root

bye

---

