---
title: "Wubi after bootloader screen"
date: 2007-05-29
forum: General Help
---

### Post by firegamer on 2007-05-29
It gives me a load of errors after "No RAID drives". I can't remember the exact error, but the code was 0x07, and prefixed with [     ##.####]. After [     98.####], It stopped erroring for a few minutes, then loaded into the shell. I'll go back in and look at the exact error and write it down then post it. This was just for if someone has the same problem as me and fixed it.. or whatever.

EDIT: Exact errors got.

[##.##] droves(usb): input/hid-core.c usb_Submit_urb fail

[##.##]hdb error code 0x70 .... logical block 123130 [[or 246261]]

Check rout = boutarg cat /proc/cmdline/
cat/proc/modules ls /dev does not exist

--
I have defragged the whole wubi folder to rid myself of error 17, but from that error I get these strings of errors.

---

### Post by ago on 2007-05-30
[http://ubuntuforums.org/showpost.php?p=2747236&postcount=12](http://ubuntuforums.org/showpost.php?p=2747236&postcount=12)

---

