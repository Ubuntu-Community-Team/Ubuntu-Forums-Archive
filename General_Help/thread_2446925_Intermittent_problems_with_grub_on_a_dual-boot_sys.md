---
title: "Intermittent problems with grub on a dual-boot system"
date: 2020-07-09
forum: General Help
---

### Post by a-shkoporov on 2020-07-09
I have a very weird intermittently occurring problem with grub on my dual boot Windows 10/Ubuntu 20.04 LTS system. I have an SSD wich has Windows 10 and EFI partition installed on it. I also have an M.2 NVME drive which is completely used for my Ubuntu installation. Every second boot I get grub shell instead of the menu. Exiting the shell brings me back to the menu, but often Windows 10 refuses to boot after that. Just black screen after I hit the menu option. If I remove my NVME from the list of boot options in BIOS, everything works perfectly, except for, I can't boot into Ubuntu any more of course. Any help is appreciated!

---

### Post by tea for one on 2020-07-09
Windows 10 and Ubuntu on separate internal disks is a good idea, however there are hundreds of threads indicating boot and/or grub problems.

My personal preference for two independent operating systems each on a separate drive is:--

Install both systems in UEFI mode.
During installation, ensure that both drives contain an EFI partition.

Many modern UEFI set up screens allow for drives to be hidden (or de-activated) when installing on one drive or the other.

It may take a reboot or two for the UEFI boot screen to re-populate each OS.

Then, you can select your OS via the UEFI boot device menu (using the dedicated key for your device).

By doing this, you can avoid some of the grub difficulties which seem quite prevalent.

If your Ubuntu installation on the nvme drive already has an EFI partition, then that may be worth exploring.

---

### Post by dragonfly41 on 2020-07-09
In addition to the good advice above I suggest also exploring [rEFInd]("https://www.rodsbooks.com/refind/") which (through LiveUSB) you can install into any EFI partition including Windows. More flexibility in booting is offered if you have preconfigured an EFI partition per drive but if not you can safely install rEFInd into your Windows EFI since /refind/ sits in a separate subfolder. Next time you create an external drive for Ubuntu remember to add a local EFI partition.

---

