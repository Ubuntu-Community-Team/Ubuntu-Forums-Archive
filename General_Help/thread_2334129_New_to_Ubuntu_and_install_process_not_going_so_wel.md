---
title: "New to Ubuntu and install process not going so well"
date: 2016-08-16
forum: General Help
---

### Post by rg000 on 2016-08-16
I have installed Ubuntu 15.10 to dual boot with Windows 10 on a usb stick and have run the installation on my computer but after the installation when it asks to restart it boots back into Windows. When I try to boot from the boot menu to the usb stick I can get to the grub2 menu it's just the only options are to install it again. I tried booting from recovery in settings in Windows 10 but it does the same thing. Help please, it's very frustrating.

---

### Post by QIII on 2016-08-16
Hello!

First things first:  It is of little use to spend much time on 15.10 since it has passed its End of Life and is no longer supported.

Can you provide the hardware specs of your machine to help us make a suggestion for which supported release you should use?

---

### Post by rg000 on 2016-08-16
Acer aspire R5-571T
Intel core i5-6200U CPU @ 2.30 ghz
8.00 gbRAM
64 bit
1tb hdd
Windows 10

---

### Post by rg000 on 2016-08-16
Going to try and dual boot 16.04 instead

---

### Post by ian-weisser on 2016-08-16
It might help if you shared your instructions with us.

Did you backup all your data before starting?
Did you disable Windows FastBoot?
Did you shrink your Windows partition?
Did you ensure both Windows and Ubuntu are using EFI and GPT instead of one using BIOS and MBR?

Dual booting can be a real pain, and can be risky for new installers. The difficulties are deliberate - Windows doesn't want to share.

For some users a VM can be easier, safer, and just as convenient. I run Windows only occasionally, in a VM instead of dual-booting.

---

