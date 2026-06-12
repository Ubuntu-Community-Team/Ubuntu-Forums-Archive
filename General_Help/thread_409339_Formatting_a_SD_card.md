---
title: "Formatting a SD card"
date: 2007-04-14
forum: General Help
---

### Post by tribble222 on 2007-04-14
I have an 8 gb SDHC card and a SDHC card reader.  I want to format my card to fat32 with 32kb clusters.  Can anyone help me with what command I need?  The device is /dev/sde1 and it mounts to /media/usbdisk when I plug it in.

Thanks!

---

### Post by tribble222 on 2007-04-14
Ok I think I figured it out:

mkdosfs -c -F 32 -n 8GB_SDHC -s 64 -S 512 -v /dev/sde1

-c has it check for bad sectors first
-F 32 tells it to make it fat32
-n 8GB_SDHC labels the volume
-s 64 puts 64 sectors in a cluster
-S 512 makes 512-byte sectors
-v gives verbose output

---

