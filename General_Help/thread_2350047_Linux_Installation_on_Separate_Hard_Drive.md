---
title: "Linux Installation on Separate Hard Drive"
date: 2017-01-20
forum: General Help
---

### Post by zeox101 on 2017-01-20
Hello, I have a question I was hoping someone could help me out with. I know that when ubuntu is downloaded as a dual boot along with windows on to a hard drive, it destroys the windows boot manager and its replaced by the GRUB menu. When you uninstall Ubuntu, you normally have to repair your windows installation to get back the boot manager since you no longer have GRUB. This may seem like an obvious question, but I just wanted to be 100% sure and get someone else's take on it. But if your computer has two hard drives, and you download ubuntu as a dual boot alongside windows on the OTHER hard drive (1 hard drive has windows, the other one has ubuntu) then this WOULDN'T destroy the windows boot manager, so if you uninstall/delete the partitions/wipe the hard drive that contains ubuntu and GRUB, the windows boot manager on the other hard drive is still intact and wouldn't require any repairing right? (I would imagine all you need to do is change a setting that makes the computer boot from that hard drive by default instead of trying to boot from the hard drive that used to contain GRUB). Anyway, thanks for reading this and helping me out!


EDIT: I can see that this probably belongs in the installation and upgrades subforum instead of general help lol, sorry I guess I overlooked that.

---

### Post by gdesilva on 2017-01-20
Depends on where exactly you instructed the Ubuntu installation to write GRUB. When you installed Ubuntu, it would have asked you which disk should be used for GRUB and if you are lucky it would have defaulted to the one on which you are installing Ubuntu - I haven't paid much attention as to whether it defaults to the one you are installing or whether it defaults to the default boot device. If you installed GRUB to default boot device (which would have been the one containing Windows unless you swapped the drives before installation) then you would need to run fixmbr from Windows installation drive otherwise, yes, pulling out the second drive should do the trick.

---

### Post by zeox101 on 2017-01-20
Thanks!

---

### Post by oldfred on 2017-01-21
Default install always installs grub boot loader to the MBR of sda. And that is where the Windows boot loader is.
That is usually what is required as Windows does not normally boot Ubuntu, but grub/Ubuntu is designed to multi-boot.

But if you have multiple hard drives, you can use Something Else install option and on partitioning screen at bottom is a combo box with choices on where to install the grub2 boot loader. Install to same drive as installing Ubuntu. 

       Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

With new UEFI systems all boot loaders are installed to the ESP - efi system partition on drive seen as sda.
That is somewhat like having an unlimited number of MBRs in BIOS boot mode for different systems.

---

