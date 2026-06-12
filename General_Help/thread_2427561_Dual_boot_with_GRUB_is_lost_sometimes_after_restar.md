---
title: "Dual boot with GRUB is lost sometimes after restart"
date: 2019-09-24
forum: General Help
---

### Post by jalik on 2019-09-24
Hello!

Sometimes when I restart my computer from my Ubuntu session (to go on windows),
the PC enters in the BIOS/EFI, without pressing F2 during boot..

At this time I don't see my SSD NVMe in the BIOS, my WIN+LINUX are installed on it.
I am forced to push the POWER button to stop the PC.

Then when I start the PC, the SSD is detected, but it boots to windows 10 directly without showing GRUB menu..
And I have to boot on a live CD to reinstall GRUB using the windows EFI partition each time...

I don't understand why and how this happen, it's not everytime,
and I am not sure if it happens after system updates...

For me it's related to the EFI.

Have you seen this before ? Do you know how to fix it ?

---

### Post by yancek on 2019-09-24
Are both windows 10 and Ubuntu installed UEFI?  That is the default for windows 10 and to boot both Ubuntu and windows 10 from Grub you need Ubuntu UEFI.

Probably the best thing to do is to use the boot repair software to provide more details on your system so that someone can help.  You can boot Ubuntu and go to the site below to get it.  Use the 2nd option described on the page to download it then run it with the Create BootInfo Summary option selected.  Do NOT try to make any repairs but post the link you get when it finishes here as that will give more details on the problem.  Do you have the default hibernation set on windows?  If so, turn it off.  Windows 10 will turn it on after some updates so you need to keep checking this after a windows update.


[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by jalik on 2019-09-24
@yancek Yes I've installed Windows + Ubuntu in UEFI using an USB KEY and also my motherboard is setup in UEFI only so it could not have boot in legacy mode.
Usually I start a live Ubuntu to reinstall manually GRUB by following this french tuto [https://doc.ubuntu-fr.org/boot-repair#installation_de_la_structure_de_boot_efi_en_lignes_de_commandes](https://doc.ubuntu-fr.org/boot-repair#installation_de_la_structure_de_boot_efi_en_lignes_de_commandes)

Yesterday I've used boot-repair directly, during the run there was an error but it managed to reinstall GRUB.
I'll see if boot-repair definitely fixed the problem or not, here is the report after fixing [http://paste.ubuntu.com/p/TX3wqGGBnK/](http://paste.ubuntu.com/p/TX3wqGGBnK/)
My dual boot is on /dev/nvme0n1 and the EFI partition is on /dev/nvme0n1p2.

About Windows hibernation I am not sure, I'll check that.

---

### Post by yancek on 2019-09-24
> About Windows hibernation I am not sure, I'll check that.

Seems you missed the below output at the bottom of the boot repair output.  Don't know that this will resolve your problem but windows updates often turn hibernation back on without informing users so you need to be aware of that.  You will not be able to mount or access any windows partition from Ubuntu or other Linux systems. 

> Windows is hibernated, refused to mount.Falling back to read-only mount because the NTFS partition is in an unsafe state. Please resume and shutdown Windows fully (no hibernationor fast restarting.)

You say that boot repair reported an error.  If you are having problems and get a specific error, always best to post the exact, complete error.  Hopefully that won't be necessary if it is now working.

---

### Post by jalik on 2020-03-27
Hi, I finally managed to fix my problem.

I thought that the bug was due to the fact that my dual boot was installed on an NVMe disk (motherboard bug or other), I could not completely exclude this track, but I know that before restarting it happened that the disk is no longer detected, and the computer entered the BIOS on its own ...

I ordered a new 2.5 "SSD (Crucial MX500).
I installed Windows 10 on another M.2 SATA SSD (WD120G Green).
Then I installed Linux on the new Crucial SSD.
At that time I still had a problem because despite the fact that I had an EFI partition for Linux, the installer took the EFI Windows partition, and when I rebooted I came across a broken grub, I tried to reinstall grub and fix it with boot-repair, but nothing ...

The trick was actually to disconnect the disk with Windows 10 (super annoying in my case because I have to dismantle the RTX 2080 and the shield of M.2 ...), then install Linux with its EFI partition, reassemble M.2 with Windows, restart on Linux and do an update-grub so that it scans the OS and adds Windows 10 to the bootloader.

So now it works nickel, no more worries about restarting, the NVMe disk serves as storage for big games and not for the OS.

In the end I think it was a Linux bug (EFI partition) and an incompatibility / bug between the CM and the NVMe in boot mode.

---

### Post by dragonfly41 on 2020-03-27
[COLOR=#000000]> The trick was actually to disconnect the disk with Windows 10 (super annoying in my case because I have to dismantle the RTX 2080 and the shield of M.2 ...),

The tip I picked up to *avoid entering the PC or laptop* is to use LiveUSB/Gparted to temporarily disable Windows boot flags then proceed to install Ubuntu in the SSD (I have the same SSD in a docking station). After installing you can restore the Windows boot flags.

[source of tip]("https://forums.linuxmint.com/viewtopic.php?t=287353")[/COLOR]

---

