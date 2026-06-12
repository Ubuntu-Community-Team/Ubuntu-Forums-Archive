---
title: "Need help getting ubuntu to run again !!!"
date: 2007-12-16
forum: General Help
---

### Post by parkland on 2007-12-16
I have an 80gb hd, partitioned 60 for data, 5 for windows, and the rest for the linux partitions.

It worked awesome, and then i had to re-install windows, and now the boot loader is gone.

It just boots windows every time.

How can i reinstall the boot loader ?

Any help on this is greatly appreciated ! :) :confused:

---

### Post by Pumalite on 2007-12-16
Boot a Live CD and post:
sudo fdisk -lu
Mount your partition and post:
cat /boot/grub/menu.lst

---

### Post by parkland on 2007-12-16
I dont have a live cd, can i download an image for a CD, or 1.44 boot disk?

I'm new to linux...

---

### Post by Pumalite on 2007-12-16
Download:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by parkland on 2007-12-16
thank you!

---

### Post by Pumalite on 2007-12-16
You are welcome and good luck.

---

### Post by PmDematagoda on 2007-12-16
Since your issue is with GRUB being overwritten from the MBR by Windows, you can just simply reinstall GRUB back to the MBR using [Super GRUB]("http://supergrub.forjamari.linex.org/?section=download").

After you reinstall GRUB you can then add the required entry to boot Windows in addition to Ubuntu.

---

