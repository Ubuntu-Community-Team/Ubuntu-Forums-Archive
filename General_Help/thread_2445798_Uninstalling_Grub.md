---
title: "Uninstalling Grub"
date: 2020-06-19
forum: General Help
---

### Post by jp734 on 2020-06-19
I have a dual boot system with lubuntu, puppy linux and Windows 10 with no EFI boot. I want to remove grub for now and will just install again later because of the windows 10 update that keeps on failing. (KB4552931 & KB4556799). Some say it's because of the boot partition. Honestly, I'm not sure if that really is the issue or not but I'm willing to take the chance because it became an annoyance. Been dealing with this failed update for months now. 

I have:
SDA1 - boot partition
SDA2 - Windows
SDA3 - Linux

sda1 is a 578MB partition that has the following files. grldr, menu.lst, menu-advanced.lst and sda_mbr.bak

How can I remove grub so the pc will boot directly to Windows. Every search I find online is for pc with EFI

---

### Post by CelticWarrior on 2020-06-19
It has nothing to do with Grub but regardless of that, in BIOS/Legacy systems with MBR, you can only remove Grub by installing the Windows bootloader in the MBR instead of Grub. So, you need to boot Windows media and do the repairs that I'm sure you'll easily find googling.

When you want to reinstall Grub after finding out the failed Windows update has nothing to do with it, you can use [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair") (2nd option, install from PPA in a normal Ubuntu live media session).

UEFI systems are much easier to handle in similar situations. All bootloaders co-exist in the ESP (EFI System Partition) and users can easily switch from one to another (e.g. boot Windows directly) in UEFI settings, boot menu options.

---

### Post by oldfred on 2020-06-19
You also have EasyBCD, which probably complicates it.
You need to look at EasyBCDs instructions and may need to undo those.

These are the standard Windows BIOS boot mode files.
Vista,  win7 and newer Windows in BIOS boot mode
  Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

These then must be from EasyBCD which uses the very old grub4dos based on orginal grub (now grub legacy) Grub2 became Ubuntu standard in 2010.

grldr, menu.lst, menu-advanced.lst and sda_mbr.bak

---

### Post by jp734 on 2020-06-19
I was hesitant to uninstall grub because @CelticWarrior backed up my hunch that it is not grub. So I opted to downloading the updates and installing them manually. Reboot after every update and when an update fails, proceed to the next update and tried to reinstall the one that failed right after a successful one. So far so good. There are a couple of updates that failed and will do more research on them but will keep in mind the suggestions you both have here.

Thanks.

---

