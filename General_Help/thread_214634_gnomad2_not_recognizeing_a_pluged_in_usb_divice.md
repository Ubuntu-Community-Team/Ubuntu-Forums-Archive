---
title: "gnomad2 not recognizeing a pluged in usb divice"
date: 2006-07-12
forum: General Help
---

### Post by Alpha_Cluster on 2006-07-12
Ok so today when i found gnomad2 i desided yay i finally can completely ditch windows.  So i went to install it and low and behold. Everytime i start it up with my Zen Xtra pluged in it tells me i dont have a player plugged into the USB bus even though when i run lsusb it says:
Bus 003 Device 006: ID 041e:4128 Creative Technology, Ltd

---

### Post by IYY on 2006-07-13
Try running gnomad2 as root:
```

gksudo gnomad2
```

---

### Post by Alpha_Cluster on 2006-07-13
I tryed that and got this error:
```
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
(gnomad2:5346): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `error == NULL || *error == NULL' failed
```
i got that in the term but the X errors i think are normal for some reason it cant find my USB?

---

