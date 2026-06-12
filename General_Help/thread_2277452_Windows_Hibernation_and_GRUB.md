---
title: "Windows Hibernation and GRUB"
date: 2015-05-09
forum: General Help
---

### Post by andrehsu6 on 2015-05-09
Whenever I hibernate, and select windows in grub when it boots up again, windows will attempt an automatic repair, and it will say that it cannot find winloader.exe. This only happens if you hibernate then try to boot into windows via grub. This resolves itself after you shutdown and boot into windows again, but the hibernated session will be lost.
Windows 8.1 x64
Ubuntu 15.04 x64

---

### Post by Jive Turkey on 2015-05-09
Windows lately, through updates, has become less friendly to dual boot systems, certain updates will not install if non-windows boot loaders are in use. I personally get around this by installing to separate physical drives and disconnecting my linux drive when I need windows to work correctly. This lets me keep the windows bootloader intact. I can still boot windows from grub with both hdd's connected, but it won't sleep if it do.

---

### Post by andrehsu6 on 2015-05-09
Hibernation work if I switch the boot order, but I'm wondering if it can be made to work in grub. Note that I'm using UEFI

---

### Post by ajgreeny on 2015-05-09
You should **never** hibernate one OS and then boot to a second OS on the same machine as you may cause many corruptions of files, and in many cases, eg, if you have a shared partition on an NTFS filesystem, you could easily completely lose an changes made to the files on that partition.

**ALWAYS DO A TOTAL SHUTDOWN** when changing from one OS to another.

---

### Post by andrehsu6 on 2015-05-09
You guys are not understanding what I am saying, here is the flow of things I am trying to do:
Hibernate Windows >>> The Laptop powers off >>> Push the power button >>> Grub shows up >>> click Windows >>> windows boots with automatic repairs >> it says windows cannot find winload.exe >>> press button to shut down >>> boot up again >>> select windows >>> boots into windows, but the hibernated session is lost
Get it now?

---

### Post by ajgreeny on 2015-05-09
Got it, but that sounds more like a Windows problem, and I certainly can't help with that as I haven't run Windows for several years.

---

### Post by andrehsu6 on 2015-05-15
Well, if you select windows as the default boot option in UEFI, it works. So is it possible for grub to boot windows the same way it does when you make the it the default boot option in uefi?

---

