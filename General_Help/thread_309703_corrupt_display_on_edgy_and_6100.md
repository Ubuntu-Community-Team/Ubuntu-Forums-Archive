---
title: "corrupt display on edgy and 6100"
date: 2006-11-30
forum: General Help
---

### Post by jetpig on 2006-11-30
I'm attempting to install edgy on an averatec 7100 series laptop.  it has a 6100, turion 64 x2 and a gig of ram.  whenever X or GDM starts the display corrupts.  occasionally it works, but for the most part it isn't usable.

any ideas

---

### Post by cronholio on 2006-11-30
If you are not offended by proprietary drivers, try to install the offical NVidia driver for your version (whatever you installed: 32 bit or AMD64):

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

### Post by jetpig on 2006-11-30
already tried those.  they made it worse than vesa.  vesa we'd get a good ddisplay every now and again, but not with the nvidia drivers.

---

### Post by jetpig on 2006-11-30
> **jetpig said:**
> already tried those.  they made it worse than vesa.  vesa we'd get a good ddisplay every now and again, but not with the nvidia drivers.

[http://www.newegg.com/Product/Product.asp?Item=N82E16834149046&CMP=AFC-Hardocp&ATT=34-149-046](http://www.newegg.com/Product/Product.asp?Item=N82E16834149046&CMP=AFC-Hardocp&ATT=34-149-046)

there's the exact laptop

---

### Post by cronholio on 2006-11-30
Please post the output of this:

```
cat /var/log/Xorg.0.log | grep "^([EW][EW])"
```

---

### Post by jetpig on 2006-11-30
The drivers were installed with automatix.

(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
(WW) The directory "/usr/share/X11/fonts/misc/" does not exist.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
(WW) 'fonts.dir' not found (or not valid} int "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom

---

### Post by arnieboy on 2006-11-30
FYI: automatix installs the nvidia drivers in the ubuntu official repositories.

---

### Post by jetpig on 2006-11-30
Ya, I like automatix alot. But this is a little beyond me.

---

### Post by jetpig on 2006-11-30
Well I changed the driver in xorg.conf to nv and x managed to start and it seemed the driver was working. However upon restart it wont boot anything and I can't get to console with Ctrl-Alt-F1. Whats the difference between the setting 'nvidia' and 'nv'?

---

### Post by cronholio on 2006-12-01
"nv" is the open.source driver for NVidia cards.

Can you boot into recovery mode (choose from Grub menu)?

---

### Post by jetpig on 2006-12-01
yes I can boot into it.  it's still set to use nv as opposed to nvidia, currently.

---

### Post by cronholio on 2006-12-01
So you boot into recovery mode and have a textmode shell? Can you try to run X?

```
startx
```

or

```
/etc/init.d/gdm start
```

---

### Post by jetpig on 2006-12-01
I managed to get it booting with the nv driver but theres no 3d acceleration.

---

### Post by cronholio on 2006-12-01
That's right, nv doesn't provide acceleration. You might want to try the NVidia installer from their site:

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

### Post by jetpig on 2006-12-01
I just tried them. Same problem.

---

