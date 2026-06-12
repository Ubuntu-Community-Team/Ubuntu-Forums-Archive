---
title: "Cant format, mount, eject USB"
date: 2012-12-07
forum: General Help
---

### Post by Blackylol on 2012-12-07
I have an USB drive that I cannot format, read, eject, format, anything. it doesnt mount but appears detected in the disk application, same in win 7, the pc knows it's there but I cannot access it.

any ideas what can i do with it? is it dead ?

---

### Post by alexandari on 2012-12-07
Sounds dead to me. But run ```
 lsusb 
``` and post the result here (when the USB drive is plugged in)

---

### Post by Kirk Schnable on 2012-12-07
> **alexandari said:**
> Sounds dead to me. But run ```
 lsusb 
``` and post the result here (when the USB drive is plugged in)

If it's showing up in the disk utility, it will most definitely show up on lsusb. 

If your data on the flash drive isn't important, you could try using the disk utility or gparted to reformat it. You say you can't format the drive... But what happens when you try?  A screenshot of that behavior will be useful.

---

### Post by Blackylol on 2012-12-10
well, it shows up in lsub but when I try to open gparted it gives me an error dev/sdc/ the device or the address doesn't exist, after some retries i cancel and it doesnt shows up.

---

