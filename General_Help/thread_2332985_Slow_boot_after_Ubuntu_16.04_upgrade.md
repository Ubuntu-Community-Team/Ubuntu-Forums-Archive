---
title: "Slow boot after Ubuntu 16.04 upgrade"
date: 2016-08-05
forum: General Help
---

### Post by cnxsoft on 2016-08-05
My computer running Ubuntu 14.04 used to boot in around 40 seconds, but after the upgrade to Ubuntu 16.04.1, it's been much slower boot in around 2 minutes.

There seems to be a big gap in of 80+ seconds in the kernel log when nothing happens.

```
[    9.776990] usb 3-4.4.2: pl2303 converter now attached to ttyUSB0
[   11.510201] floppy0: no floppy controllers found
[   98.444400] vboxdrv: Found 8 processor cores
[   98.460319] vboxdrv: TSC mode is Invariant, tentative frequency 4026996449 Hz
[   98.460321] vboxdrv: Successfully loaded version 5.0.26 (interface 0x00240000
```


A two services take around 8 seconds each, but the rest looks pretty fast:
```
systemd-analyze blame
          8.121s apt-daily.service
          7.658s NetworkManager-wait-online.service
           931ms docker.service
           710ms winbind.service
           695ms nmbd.service
           647ms samba-ad-dc.service
           543ms ModemManager.service
```

Anything else I should look at?

---

### Post by oldfred on 2016-08-05
One user years ago found that he had floppy drive set on in BIOS, but had no floppy and that caused issues.
Check that you do not have a floppy drive on in BIOS.

Another found that he left a non-bootable DVD in player and it wanted to run fsck on DVD, as if it could.
So if you do have a floppy make sure it is empty.

---

### Post by cnxsoft on 2016-08-08
Thanks. I finally found my issue using systemd-analyze plot > filenamexxx.svg
I had a serial to USB device based on PL2303 attached which slowed the boot considerably.

With PL2303

Kernel around 5 second, user space over 3 minutes:
Boot chart -> [https://mega.nz/#!K8IU3Aha!TOtoJTt4lcIwWRy4ci2SXNlEaXQm41FJro91GLSelkw](https://mega.nz/#!K8IU3Aha!TOtoJTt4lcIwWRy4ci2SXNlEaXQm41FJro91GLSelkw)


Without PL2303:
systemd-analyze
Startup finished in 5.764s (kernel) + 11.282s (userspace) = 17.047s
Boot chart -> [https://mega.nz/#!60wUBahZ!nMMVhDs2YucL8jLhhOytg78xMTezXuI2x3fr_z0HACI](https://mega.nz/#!60wUBahZ!nMMVhDs2YucL8jLhhOytg78xMTezXuI2x3fr_z0HACI)

---

