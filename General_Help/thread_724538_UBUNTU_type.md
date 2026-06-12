---
title: "UBUNTU type"
date: 2008-03-14
forum: General Help
---

### Post by fusion2344 on 2008-03-14
How can I determine which UBUTNU I have (Feisty or Edgy)?

---

### Post by bilal.17 on 2008-03-14
click on system then about ubuntu .. it should state which version you have

---

### Post by StOoZ on 2008-03-14
in terminal:
> lsb_release -c

---

### Post by fusion2344 on 2008-03-14
Cool, thnx.

lsb_release did the job.

Maybe you can give me some suggestions.

I need to monitor (sniff) USB communications on UBUNTU Edgy (kernel 2.6.17-11-generic) with usbmon.
I've read that I need to add USB support to the kernel settings (make menuconfig).
I looked in my source directory and found only the header files.
What is the best method to get the kernel source files into my source directory?

After menuconfig, is it necessary to re-compile the kernel?

Thanks

---

### Post by ryanhaigh on 2008-03-14
You will need to recompile the kernel after making any changes

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

Are you sure you need to do this to do what you want, does the default kernel not use the option you need?

---

### Post by fusion2344 on 2008-03-14
Well the things is I need usbmon on my system.

According to other posts (from another forum), one need to activate USB debug support to get submon on the system.

Unless you know about another way to get usbmon on the system?

---

### Post by ryanhaigh on 2008-03-15
Looking at the config used for the kernel it appears as though those posts are correct. Compiling the kernel doesn't take that long, just download the ubuntu sources, make the changes and recompile.

```
cat /boot/config-2.6.22-14-generic | grep USB | grep DEBUG
# CONFIG_USB_DEBUG is not set
# CONFIG_USB_STORAGE_DEBUG is not set
# CONFIG_DVB_USB_DEBUG is not set
# CONFIG_USB_GADGET_DEBUG_FILES is not set
# CONFIG_USB_PWC_DEBUG is not set
CONFIG_USB_SERIAL_DEBUG=m
# CONFIG_VIDEO_PVRUSB2_DEBUGIFC is not set
```

---

