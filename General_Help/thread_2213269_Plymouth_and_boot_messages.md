---
title: "Plymouth and boot messages"
date: 2014-03-25
forum: General Help
---

### Post by Questionario on 2014-03-25
Hi,

I have installed a mini-iso of Ubuntu 13.04, upgraded to 13.10 in order to run XBMC (mediacenter) on it.
I installed plymouth to get a splash screen, which works but before the splash screen I get some messages as well as after the splash screen right before XBMC starts.
I got rid of the ones after the splash screen (put loglevel=2 and console=tty10 into /etc/default/grub) but I get the following messages before the splash screen (not even sure if I should worry about them as the USB-harddrive works fine).
below is an extract of dmesg, only the bold part seems to appear on screen though.
```
[    4.627368] scsi 6:0:0:0: Direct-Access     WD       My Passport 0748 1025 PQ: 0 ANSI: 6
[    4.627931] scsi 6:0:0:1: Enclosure         WD       SES Device       1025 PQ: 0 ANSI: 6
[    4.628510] sd 6:0:0:0: Attached scsi generic sg1 type 0
[    4.628680] sd 6:0:0:0: [sdb] 3906963456 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    4.628778] scsi 6:0:0:1: Attached scsi generic sg2 type 13
[    4.629517] sd 6:0:0:0: [sdb] Write Protect is off
[    4.629527] sd 6:0:0:0: [sdb] Mode Sense: 47 00 10 08
[B][    4.630211] sd 6:0:0:0: [sdb] No Caching mode page found
[    4.630815] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    4.634973] sd 6:0:0:0: [sdb] No Caching mode page found
[    4.635578] sd 6:0:0:0: [sdb] Assuming drive cache: write through[/B]
[    4.637338]  sdb: sdb1
[B][    4.639847] sd 6:0:0:0: [sdb] No Caching mode page found
[    4.640469] sd 6:0:0:0: [sdb] Assuming drive cache: write through[/B]
[    4.641159] sd 6:0:0:0: [sdb] Attached SCSI disk
[    4.680514] ses 6:0:0:1: Attached Enclosure device

```

does anyone know how I can get rid of these messages? preferably showing the splash screen the whole time and not just a black scren when the messages usually appear (thats the way it is not except with the messages mentioned above)

---

### Post by Questionario on 2014-03-27
bump :(

---

### Post by Questionario on 2014-03-31
noone seen this before?

---

### Post by grahammechanical on 2014-03-31
What you are seeing are Linux system messages. Linux has to load to a certain level before it can load something like Plymouth and its splash screen. It is all part of the way that Linux is put together. First Grub, then Xserver, then the video driver, then Plymouth, then LightDM and onwards.

The Grub boot parameter should already have "quiet splash" and those two entries should minimize this effect. This situation will remain like this until Ubuntu switches over to the Mir display manager. It is supposed to replace Xserver, LightDM and even Compiz. Hopefully then the loading process will seem much smoother.

Regards.

---

