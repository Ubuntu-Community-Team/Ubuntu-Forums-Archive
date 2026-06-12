---
title: "How to install Windows 11 having Ubuntu 20.04?"
date: 2023-11-04
forum: General Help
---

### Post by 0x23587 on 2023-11-04
[COLOR=#0C0D0E][FONT=-apple-system]I have Ubuntu 20.04 in an HP Spectre x360-13-ae052nr laptop. I have enabled booting from USB on BIOS configuration and I have tried to boot from the USB with Windows 11, but it does not boot from the USB and starts in Ubuntu 20.04.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]I would like to know how I could install Windows 11 on my laptop having Ubuntu 20.04 installed. I don't want a dual boot. I want to switch from Ubuntu 20.04 to Windows 11.[/FONT][/COLOR]

---

### Post by MAFoElffen on 2023-11-04
You said you do not want a dual boot... Do you mean that you do not care if Windows 11 erases and replaces your Ubuntu 20.04 Installation with itself?

---

### Post by tea for one on 2023-11-05
As you power on the PC, tap F9 at, for example, one second intervals.
You should arrive at the HP boot menu.
Select your Windows installation USB.

---

### Post by yancek on 2023-11-05
If you saved the change in the BIOS to boot from the USB, it should boot windows.  How did you put the windows installation files on the USB?  You should be able to use Rufus (and probably other software to do this.  Do you have another computer to test boot the usb to eliminate that as a problem?  Do you select or have an EFI boot option in the BIOS?

---

### Post by MAFoElffen on 2023-11-05
Actually, for this 3 year old HP... It came with Windows 10 Pro... If your goal is to reload it fresh as just having Windows (with no other OS) with the license being activated...

The generic HP boot meneu hot-keys are <Esc> or <F9>... and choose to boot from the Installer on the USB flash drive.

Install Windows 10 Professional. Windows OS'es are not "other OS" aware and will erase everything else on the internal disk. After the install, and first boot, go to activate and it will activate the license, because the digital key is written to the motherboard. It will activate.

Then go to Updates ad Upgrade the release to Windows 11. This way, you will end up with Windows 11 and it will be activated.

I do not know why you are at an Ubuntu Support Forum, asking how to install Windows as the only OS... But there you go.

If you wanted to keep your Ubuntu OS, you would have to backup your install. Install Windows. Make room for the other OS by shrinking the partitions from within Windows. Then restore Ubuntu in the space you created as unallocated. Then repair/reinstall a grub menu.

---

