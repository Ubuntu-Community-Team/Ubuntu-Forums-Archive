---
title: "NTFS &amp; External HDD"
date: 2007-06-26
forum: General Help
---

### Post by tombiz on 2007-06-26
Which is better for the external HDD NTFS support.

The ntfs-3g or the ntfs driver that comes with AUTOMATIX?

---

### Post by AlexThomson_NZ on 2007-06-27
I'm not sure what one comes with Automatix, but ntfs-3g is better than the kernel default one as it allows writing to the hard drive.  If Automatix allows this writing, it would be using the ntfs-3g driver.

---

### Post by compiledkernel on 2007-06-27
The ntfs-3g is indeed the Fuse NTFS driver and default for use with NTFS devices. 

sudo apt-get install ntfs-3g ntfs-config 

to get the driver and the GUI for configuring it.

---

### Post by Qu4k3R on 2007-06-28
Automatix use ntfs-3g (i think so)
I am using ntfs-3g up to 7 months (and I did never got problems)

---

