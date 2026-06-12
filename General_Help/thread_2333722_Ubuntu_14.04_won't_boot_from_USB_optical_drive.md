---
title: "Ubuntu 14.04 won't boot from USB optical drive"
date: 2016-08-12
forum: General Help
---

### Post by tcomdog on 2016-08-12
I have a Toshiba Satellite L850, Ubuntu 14.04 only installed and a LGSlim Portable DVD writer 2.0 USB. The DVD writer is recognized andworks if I am running Ubuntu and I plug it in, but Ubuntu will notboot from the USB external writer drive.


Needless to say I am using this drive because my internal drive seemsto have gone bad.

---

### Post by sudodus on 2016-08-12
Welcome to the Ubuntu Forums :-)

I think your computer should boot from your USB connected DVD as well as from a USB pendrive, maybe easier from a USB pendrive.

Is it running in UEFI mode or BIOS mode? You can check according to the this link,

[Installation/FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

```
test -d /sys/firmware/efi && echo efi || echo bios
```

Some newer Toshibas are tricky in UEFI mode (but my Toshiba from 2013 lets me select boot drive after pressing the F12 key directly at boot).

---

