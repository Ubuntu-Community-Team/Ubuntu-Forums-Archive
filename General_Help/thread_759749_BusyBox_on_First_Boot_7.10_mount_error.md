---
title: "BusyBox on First Boot 7.10 mount error"
date: 2008-04-19
forum: General Help
---

### Post by netharis on 2008-04-19
Hi, I have just downloaded the 7.10 of Ubuntu, and i tried to boot it. I select the Start or Install Ubuntu choice and it shows the loading splash screen. After that, it just boots into BusyBox.
The tail of casper.log says:
```
stdin: I/O error
stdin: I/O error
stdin: error 0
/init: /init: 1: cannot open /dev/scd0: no medium found
/init: /init: 1: cannot open /dev/scd0: no medium found
stdin: I/O error
mount: Mounting /dev/loop0 on //filesystem.squashfs failed: No such device
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesyste.squashfs
```z

I am running on a 3,4Ghz, 2GB DDR2, Asus P5WDH Deluxe, PCX5600 VC, and 3 HDD's (300,250,120) - SATA's
Also note that i was running ubuntu for some time (7.04, via wubi) and i didn't had any problems

Any idea?

Thanx

---

### Post by prshah on 2008-04-19
> **netharis said:**
> 
```
stdin: I/O error
stdin: I/O error
stdin: error 0
/init: /init: 1: cannot open /dev/scd0: no medium found
/init: /init: 1: cannot open /dev/scd0: no medium found
stdin: I/O error

```
Any idea?


I'd say CD error considering the error messages. There is an option to check the CD integrity in the startup menu; have you tried that?

---

