---
title: "[SOLVED] Ubuntu hangs regularly"
date: 2007-08-06
forum: General Help
---

### Post by clum on 2007-08-06
Hello,
I recently installed Ubuntu (7.04) on my computer. I am overall very pleased with it, and would like to continue using it. However, I have one major problem - every 45 minutes or so, the computer hangs! This happens when doing completely innocent things, like reading web pages, etc. Everything, including the mouse cursor, stops. It stops responding to the keyboard, too, including Ctrl-Alt-Backspace, and the like. The only thing I can do is to hard-reset by holding down the power button. I have installed other versions of linux on many occasions without such problems. I also have WindowsXP installed on the same computer with no problem. The only thing I've tried is disabling the screen saver and the monitor automatically turning off in the Gnome power preferences, which are the only periodic things I could think of, to no avail.
Here is a general profile of the computer:

Dell Dimension 8100
Pentium 4 1.3 GHz
256Mb RAM
Modem: USB Wireless DRUC-U3 installed with ndiswrapper (I mention this because this does get randomly disconnected in Windows, and then I have to unplug and replug it.)
After I installed (and set up ndiswrapper), I selected all new upgrades in Synaptic and downloaded them. I've also installed a couple of things like Privoxy and Nvidia-glx drivers, through synaptic.
An interesting notice I receive every time I boot the computer (I used to get the same message in Knoppix), even before it comes up with the Ubuntu logo, is something about and null local APIC table and that it's disabling SMP (I only have one processor) and that I should tell my hardware vendor. When I used to get this message in Knoppix, I was always suspicious of it, because I have a Dell computer, which generally doesn't have faulty hardware.
I've had some strange problems with USB in previous versions of Linux, though none in this. My mouse and keyboard are on the USB1.1 ports that came with the computer (it complains or doesn't work properly if I connect it elsewhere) and my scanner, printer, and wireless network card are on USB2.0 ports which I installed myself.

Thank you very much,
Clum

---

### Post by nitro_n2o on 2007-08-06
you should use the ubuntu 32 bit edition (the normal one) and  you should have enough disk space.. if the disk is jammed will cause serious problems..

---

### Post by clum on 2007-08-06
I am most certainly using the 32-bit addition, and I have lots of space.

---

### Post by nitro_n2o on 2007-08-06
can you find any skeptical error messages in /var/log/syslog this should help

---

### Post by clum on 2007-08-06
No, there are no messages at all near the times when the computer hangs (until afterwards, when I boot up again). However, I did find in there the message I always get when booting: 
SMP mptable: null local APIC address!
BIOS bug, MP table errors detected!...
... disabling SMP support. (tell your hw vendor)
grep APIC also found the following:
Local APIC disabled by BIOS -- you can enable it with "lapic"
mapped APIC to ffffd000 (0120a000)
Local APIC not detected. Using dummy APIC emulation.

---

### Post by nitro_n2o on 2007-08-06
well.. check out this [http://ubuntuforums.org/showthread.php?t=27245&page=2](http://ubuntuforums.org/showthread.php?t=27245&page=2)

---

### Post by clum on 2007-08-07
Hmmm, I'll try it, though noapic seems more appropriate than acpi=off.

---

### Post by clum on 2007-08-07
No, I'm afraid it didn't help. It just hung again. This time I'm trying noapic. I'm also wondering whether it might have to do with the fact that I compiled ndiswrapper against the 2.6.20-15 kernel that Ubuntu came with, and I'm not running the 2.6.20-16 kernel that it upgraded to. I'm not sure, but I don't think it hung before I did the upgrade, or at least not as often. Maybe I should go back to 2.6.20-15, or recompile ndiswrapper.

---

### Post by clum on 2007-08-07
Hmmm...It just did it again. I've gone back to the 2.6.20-15 kernel to see if that helps.

---

### Post by clum on 2007-08-07
Well, I've been in the older kernel now for over an hour, and it still hasn't hung. I'm going to go back to this kernel permanently and hold back the kernel package.

---

