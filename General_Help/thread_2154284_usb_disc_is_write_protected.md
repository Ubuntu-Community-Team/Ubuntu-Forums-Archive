---
title: "usb disc is write protected"
date: 2013-06-14
forum: General Help
---

### Post by Komir on 2013-06-14
Hello, I have problem with my verbatim usb (8gb). Dont know why , when try to format, get 
```
dd: opening ‘/dev/sdc’: Read-only file system
```


Stick dont have switch to enable/disble protection.
On
```
sudo hdparm -r0 /dev/sdc1
```

Get
```
/dev/sdc1:
 setting readonly to 0 (off)
 readonly      =  0 (off)
```

Best regards

---

### Post by 3rdalbum on 2013-06-14
The output of dmesg would help here, but it looks like your stick is being mounted read-only. This could be due to one of two factors:

1. Somehow Ubuntu is set up incorrectly to mount it as read-only instead of the default read-write (unlikely)
2. There is filesystem damage on the stick (most likely)

How are you trying to format it? Have you tried using Gparted to format it, as this won't require it to be mounted?

---

### Post by Komir on 2013-06-15
Hello, thanks for your help. In attach is dsmeg log. Problem is with Verbatim STORE N GO usb.

Best regards

---

