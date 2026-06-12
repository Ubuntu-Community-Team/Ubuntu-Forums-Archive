---
title: "Cannot boot Ubuntu LTS after hardware change"
date: 2021-06-09
forum: General Help
---

### Post by chadosaurus on 2021-06-09
Hello, I have installed ubuntu onto a USB drive a couple years ago, mainly as a backup for windows in case something goes wrong, but I also had other uses for things windows couldn't do.

I've recently switched over to all new hardware onto my PC (AMD Mobo switched from intel). After a bit of work I was able to get my old windows install to work optimally with the new hardware. Today I needed to use my ubuntu usb drive, and thought I'd give it a try, but it does not work. I can boot into grub fine, no problem, but when I try any option such as Ubuntu recovery it will go into the black boot up screen, coming up with a bunch of errors, which I kind of expected.

Then it stalls at initramfs, awaiting some input. Problem is my keyboard no longer works at this point. All the keyboards I have at home are usb, and none of them seem to work at this screen. I have tried the "recovery option in grub, and the booting into an older version of ubuntu, all with the same results.

I was googling some things and it looks like some people used the "live CD" to fix their issues, but I am unsure if this will work for me seeing as my drive is on a USB as it is...

Is there a way to put the live CD on the same USB and launch it with grub (which is also on that usb stick), or should I go a different route? I am a serious noob when it comes to Ubuntu (linux in general), so please be patient with me. Thank you!

---

### Post by sudodus on 2021-06-09
- Which version of Ubuntu is there in your USB drive?

- Is there some proprietary driver installed in your Ubuntu (in the USB drive)? Examples: graphics driver or wifi driver. It is also possible that some hardware on the new motherboard needs a proprietary driver.

- Is your new system booting in UEFI mode with secure boot enabled? In that case, maybe it will work if you disable secure boot.

- Is your new system using the same interface to the HDD or another one (SATA or NVME)?

[hr][/hr]
It is more likely to work, if you try a current version of Ubuntu **live** (cloned from the iso file to a USB pendrive).

- It the motherboard is very new, you may need the newest possible version, Ubuntu 21.04. But I suggest that you start by trying with 20.04.2 LTS, because it has longer support until end of life (until April 2025 versus 9 months).

- Try with the [boot option](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808) [FONT=Courier New]**nomodeset**[/FONT], if there are problems also with the live drives.

---

