---
title: "UbuntuStudio will not load"
date: 2007-05-19
forum: General Help
---

### Post by octoberdan on 2007-05-19
UbuntuStudio will not load on my Acer Aspire 5100-5033. It installs without complaint, but it hangs soon after the splash screen appears. If I cntrl-alt-f1, the only two messages are "PCI: BIOS BUG #81[49435000] found" and "Loading, Please Wait"

Any help or comments will be greatly appreciated. Thank you.

---

### Post by rocket777 on 2007-05-22
Did you need any special kernel options to get the install to run?

I did (nosmp, noapic, nolapic) on my amd system, and unlike in feisty install from live cd, I found that the options were not copied to the menu.lst grub file. So, after the install, the first reboot would hang at the first tick of the progress bar on the splash screen.

My fix was to enter grub at boot time and edit the kernel line. Then I had to do it again after the system booted, by going into /boot/grub/menu.lst and edit in the options there as well.

---

### Post by octoberdan on 2007-06-14
> **rocket777 said:**
> Did you need any special kernel options to get the install to run?

I did (nosmp, noapic, nolapic) on my amd system, and unlike in feisty install from live cd, I found that the options were not copied to the menu.lst grub file. So, after the install, the first reboot would hang at the first tick of the progress bar on the splash screen.

My fix was to enter grub at boot time and edit the kernel line. Then I had to do it again after the system booted, by going into /boot/grub/menu.lst and edit in the options there as well.

Thank you for the response! I was just about ready to wipe out the partition and beggin my work on "Hackbuntu" (Ubuntu based Trackback2 like OS for penetration testers), but then I stumbled on your response! 
How has needing those options affected your performance?
Thanks again...

---

### Post by radiobuzzer on 2007-12-09
Thank you. I had the same problem in an ACER 5102 laptop, with a fresh clean installation of Ubuntustudio 7.10 . I noticed that the boot didn't exactly halt, but it was waiting for ANY key to be pressed (including Alt, Ctrl etc.) in order to proceed from the one boot step to the other. Therefore, if I kept pressing the Alt key, the system boot up perfectly and really fast. Weird.

It was fixed by added these parameters in the default kernel.

My desktop didn't have this problem though, and it boots perfectly. Therefore, it is a good idea to be specified as a bug

---

### Post by prodigalson666 on 2007-12-19
> **rocket777 said:**
> Did you need any special kernel options to get the install to run?

I did (nosmp, noapic, nolapic) on my amd system, and unlike in feisty install from live cd, I found that the options were not copied to the menu.lst grub file. So, after the install, the first reboot would hang at the first tick of the progress bar on the splash screen.

My fix was to enter grub at boot time and edit the kernel line. Then I had to do it again after the system booted, by going into /boot/grub/menu.lst and edit in the options there as well.

What did you add or take away from the kernal line when you edited it to make it work?

---

