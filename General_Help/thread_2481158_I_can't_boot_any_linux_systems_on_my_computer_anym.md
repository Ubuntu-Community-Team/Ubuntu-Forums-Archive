---
title: "I can't boot any linux systems on my computer anymore"
date: 2022-11-20
forum: General Help
---

### Post by ash22 on 2022-11-20
I have a PC with Linux on one drive and Windows on the other. I can boot into Windows like normal, but now I can't boot into my Linux system or any Linux operating system. I tried to fix this by installing Boot Repair on a flash drive. I make the system boot into the flash drive and I select 'English' from the language list, and a then a black screen. Sometimes there are some messages before the blank screen. I couldn't boot into Boot Repair, so I burned a live CD into a DVD and the same thing happened. Either lines of error messages, or blank screens.

The messages
```
ACPI error could not resolve
```
```
ACPI BIOS ERROR
```
```
ACPI error: aborting method
```
```
\SB.PCI0.GPP2.PTXH.RHUB.POT*._PLD due to previous error
```

---

### Post by grahammechanical on 2022-11-20
Which drive has the boot priority? The Windows drive or the Linux drive? Which drive has the EFI System partition? The Linux bootloader (Grub) should have boot files in the EFI System partition on the drive that has boot priority.

Regards

---

### Post by ash22 on 2022-11-20
> **grahammechanical said:**
> Which drive has the boot priority? The Windows drive or the Linux drive? Which drive has the EFI System partition? The Linux bootloader (Grub) should have boot files in the EFI System partition on the drive that has boot priority.

Regards
The BIOS says that the 1st priority drive is the one with Windows. How can I check the EFI system boot files?

---

