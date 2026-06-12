---
title: "If I reset windows, will it reset ubuntu 14.04?"
date: 2015-09-19
forum: General Help
---

### Post by essxiv on 2015-09-19
Hey guys,

I want to delete everything from my Windows 8.1 OS, but I want to keep EVERYTHING on my Linux OS.
If I reset my Windows, will it also delete my Linux?

Thanks.

---

### Post by Bucky Ball on 2015-09-19
How do you mean you want to delete everything? You want to completely erase Windows?

---

### Post by essxiv on 2015-09-22
> **Bucky Ball said:**
> How do you mean you want to delete everything? You want to completely erase Windows?

Not completely erase the Windows OS, but just reset all of the content/settings. Basically wiping and resetting Windows, but I do NOT want it to affect anything on my Ubuntu OS.

---

### Post by Bucky Ball on 2015-09-22
It won't. They are not related. If you have booted Windows, the Ubuntu partition has nothing to do with it. 

The only thing it may do if you upgrade, say from Win8 to Win10, or reinstall Windows is install its boot manager over grub and screw the boot of Ubuntu. This is fixable. This has nothing to do with altering anything on the Ubuntu partition. It is about the MBR or EFI partition. 

As for changing things while booted into Windows, that has nothing to do with the Linux partition. It won't even be mounted I wouldn't think.

---

