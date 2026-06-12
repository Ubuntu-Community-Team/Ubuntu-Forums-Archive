---
title: "trying to format a locked micro sd card"
date: 2016-03-28
forum: General Help
---

### Post by mhingston on 2016-03-28
Can anyone help me please. I am trying to format a micro SD card. both windows and Ubuntu says card is read only. I can't change it to read / write.I get this message when I try formatting.
Error creating file system: Command-line `mkfs.vfat -I -n "" "/dev/sdg"' exited with non-zero exit status 1:
stdout: `mkfs.fat 3.0.28 (2015-05-16)
'
stderr: `mkfs.vfat: failed whilst writing reserved sector
' (udisks-error-quark, 0)

I'm not very good with command line interface so any ideas would be most grateful.

---

### Post by QDR06VV9 on 2016-03-28
Typically when a SD card goes into write protected state it's because the card is about to fail completely. This is a safety measure so you can recover data before it completely dies.
One last try you can use is the SD Card formatter from the SD association. Works with any manufacturer's card...but sadly it is a Windows or Mac only application.
[https://www.sdcard.org/downloads/formatter_3/](https://www.sdcard.org/downloads/formatter_3/)

If this can't format, then the card needs replacing.

Oh, there is one other cause - if you've put this in a full sized SD card adapter, and that adapter has the "lock" switch put down, it will also cause this.
Kind Regards

---

