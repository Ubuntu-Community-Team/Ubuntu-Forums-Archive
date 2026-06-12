---
title: "BIOS not recognizing external hard drive"
date: 2007-12-26
forum: General Help
---

### Post by JohnnyBoy022 on 2007-12-26
I installed Ubuntu 7.10 on an external usb hard drive. When I tried to use my BIOS one time boot menu to boot from the external drive, it did not show up. I used SuperGRUB disk to select boot Linux from the external drive. The compputer restarted and I went to the BIOS one time boot menu and the option USB Device showed up. I selected that and the grub screen came up, and I could boot Ubuntu just fine. However, when I turn off my computer, unplug the external drive, and plug it back then try to boot from it again, I no longer have the option to boot from USB Device. It is almost like half of the time my BIOS is recognizing the device and half the time it is not. I know my BIOS is capable of booting from it but I don't want to go throught the trouble of booting into the superGRUB disk first just to boot into Ubuntu. Does anyone know a way to get my BIOS to recognize the drive all the time?

---

### Post by Craigus on 2007-12-26
Does this happen if the USB device is already plugged in when the computer is powered on ?

---

### Post by JohnnyBoy022 on 2007-12-26
Every time I have tried it, the USB device was plugged in when the computer was turned on. I haven't tried plugging it in after I turn the computer on.

---

### Post by Craigus on 2007-12-26
What happens if you power up, get into BIOS, and then restart - does the external drive show up then ?

---

### Post by JohnnyBoy022 on 2007-12-26
I don't think I have an option to reboot from the BIOS. The only way to restart is to hold the power switch for a few seconds then turn it on again.

I also tried booting into windows, then I clicked "safely remove hardware" to remove the external drive. But I left it plugged in. I restarted the computer and the grub screen came up. I was able to boot into Ubuntu just fine.

It seems like there isn't enough time for the bios to realise that there is an operating system on the drive.

---

### Post by Craigus on 2007-12-26
Not really a solution, but ctrl-alt-del from inside the BIOS screens may restart.
There should also be a save / don't save and restart option in the BIOS somewhere.

---

### Post by JohnnyBoy022 on 2007-12-27
I tried booting up, waiting for 30 seconds in the BIOS, and restarting using ctrl-alt-delete. Ubuntu booted up just fine.

I'm fairly sure now there just isn't enough time for the bios to recognise the drive. Now I just need to find a way to fix it. Any ideas?

---

