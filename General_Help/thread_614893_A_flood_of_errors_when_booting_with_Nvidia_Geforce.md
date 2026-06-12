---
title: "A flood of errors when booting with Nvidia Geforce 6200"
date: 2007-11-16
forum: General Help
---

### Post by Githlar on 2007-11-16
System Specs:
Operating System: Ubuntu 7.10 (Gutsy Gibbon)
Computer Brand/Model: HP a705w
CPU: 2.93Ghz Intel Celeron
Chipset: Intel 845GV
RAM: 1GB DDR1-333 SDRAM (2x512MB)
Onboard Video Adapter: Intel Extreme Graphics (8MB max shared memory)(The website for this machine says that it has up to 64MB shared memory, but it lies)
PCI Video Adapter: Nvidia GeForce 6200 (Rebranded under Jaton Corporation with model number VIDEO-338PCI-DVI)

OK, here's the deal. I just installed my new 256MB Nvidia GeForce 6200 PCI video card. The computer will start just fine as long as the video adapter is not set to PCI in the BIOS. But in this mode, I get no graphical benefits at all and I'm stuck with 8MB on-board video. So, I set my BIOS to use PCI as the video adapter and started Ubuntu. It started loading and stopped after about two bars on the loading screen I think. So, I rebooted into recovery mode and watched what happens. Very soon after the "*Preparing Restricted Drivers..." (I think there might be a couple after that, but they're very quick) I get a huge flood of errors and the boot process halts. I had the very same problem with my 128MB ATI Radeon 9250 PCI video card (witch did not have Linux drivers because it was too old). With my Radeon, I traced it down to the Modprobe udev rules (/etc/udev/rules.d/90-modprobe.rules). I found the specific rule in Feisty, but I don't see anything that triggers my memory here in Gutsy. When I disabled the rule in Feisty however, modprobe/udev failed to notice a lot of hardware and things just didn't work correctly.

I'm really hoping one of your Linux Gurus knows what's going on here or a possible resolution? My experience level is probably expert beginner. I know some about the back-end, but not a whole lot. Since the same problem (or what appears to be the same problem) occurred with both video cards of different brands, this leads me to believe it is a hardware problem other than the video card. My (amateur) guess is that it is due to some deviation from a standard (just like the ACPI control on this machine - I have to run Linux with the noacpi kernel parameter). I really hope somebody can sort this out for me. It has proven to be a major headache with my Radeon and I never got it to work anyway.

Regards,
Githlar

---

### Post by Githlar on 2007-11-17
Modified post. Bumping.

---

### Post by Githlar on 2007-11-21
Apparently, my onboard Intel video was loaded by modprobe and then it tried to use the video card and probably created some kind of conflict. I resolved the issue by adding this to /etc/modprobe.d/blacklist:
```
#Blacklist onboard Intel drivers
blacklist agpgart
blacklist intel_agp
```

---

