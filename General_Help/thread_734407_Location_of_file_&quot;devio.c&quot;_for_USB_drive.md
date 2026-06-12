---
title: "Location of file &quot;devio.c&quot; for USB drivers"
date: 2008-03-24
forum: General Help
---

### Post by swapnova on 2008-03-24
Hi guys, 

I've been trying snoop USB port activity and print it out in the kernel's log file. I'm looking for the files inode.c, devices.c, and devio.c. They should all be located in the kernel's source tree under drivers/usb/core. However, there is only a Kconfig and a Makefile in the directory. I've looked in the following two places in my machine: 

/usr/src/linux-headers-2.6.22-14/drivers/usb/core
/usr/src/linux-headers-2.6.22-14-generic/drivers/usb/core

But there's nothing...

---

### Post by geraldm on 2008-03-24
Use the find command
```

 find $LIN/drivers/usb -name "devio.c" -print

```
$LIN is an ENV variable in MY LOCAL system set to the top kernel source directory for the kernel that is running.  The cmd returns:
/home/pkg/build/linux/linux-2.6.24.2n/drivers/usb/core/devio.c
The files are all in that directory.  You should be in the source, not the kernel-headers package.

Gerald

---

