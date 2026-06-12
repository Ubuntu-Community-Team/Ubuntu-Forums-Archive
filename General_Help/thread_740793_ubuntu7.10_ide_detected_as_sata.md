---
title: "ubuntu7.10 ide detected as sata"
date: 2008-03-31
forum: General Help
---

### Post by darkz_ on 2008-03-31
hello
i'm running ubuntu 7.10 w/  2.6.22-14-generic and my ide drive is detected as a sata drive
problem is, it gives quite bad performance:
```

:/dev$ sudo hdparm -tT /dev/sda
/dev/sda:
 Timing cached reads:   418 MB in  2.00 seconds = 208.52 MB/sec
 Timing buffered disk reads:  172 MB in  3.01 seconds =  57.15 MB/sec

```

how do i fix this? thanks in advance.

---

### Post by sekinto on 2008-03-31
Does your grub configuration file (/boot/grub/grub.conf) use /dev/hda or /dev/sda.
If it uses /dev/hda and everything is booting properly (I assume it is), then you might want to see if your /etc/fstab file points to /dev/hda or /dev/sda. If it points to /dev/sda you might want to change it to /dev/hda.

If that messes anything up you can change the h back to an s from a live CD or something.

---

### Post by darkz_ on 2008-03-31
in grub configuration file it's hd0,0 & was sda in /etc/fstab 
i changed the fstab to hd, like you said -- it didnt mess anything up, but suprisingly didn't change anything either

---

