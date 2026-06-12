---
title: "Problems installing Ubuntu 13.10 on Windows 8 Machine"
date: 2014-01-09
forum: General Help
---

### Post by nickmoore_1 on 2014-01-09
I am trying to install Ubuntu 13.10 on to a HP 2000 running windows 8. I have tried booting from live usb and from a disk and even from the disk that came with the ubuntu unleashed book. I follow the instructions and when it comes time to reboot so I can finish installing ubuntu and select the ubuntu os from the menu it goes to a black screen and then comes up with an error saying to fix the boot and that ubuntu files are missing. What am I doing wrong?

---

### Post by grier-devon on 2014-01-09
Did you look at the boot sequence? Are you using bios or UEFI? IF using UEFI you may want to consider using the legacy boot sequence offered, that is how I got Ubuntu to boot on an HP recently.

---

### Post by nickmoore_1 on 2014-01-09
I am using UEFI, I have seen that mentioned, but the only thing it said was to turn it off then back on again.

---

### Post by grier-devon on 2014-01-09
Okay, what I had to do was turn on Legacy mode and then set the disc drive to boot first. Install Ubuntu and once done then go back in and keep it on Legacy mode but set HDD to boot first. It is a weird time with Linux since the UEFI since it has required a little more then normal Linux work around, this is just because it is a newer technology. For this reason this is why my next computer will be from System76. If this does not work and let me know and we will continue to trouble shoot:P, I am sure the answer is simple, if this does not work then do me a favor and post your system specs please.

---

