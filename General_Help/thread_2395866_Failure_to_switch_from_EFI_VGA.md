---
title: "Failure to switch from EFI VGA"
date: 2018-07-07
forum: General Help
---

### Post by &amp;*@Fth&amp;% on 2018-07-07
So I've got a weird one for you: my computer only *sometimes* successfully switches from EFI VGA to AMDGPU ("fb: switching to amdgpudrmfb from efi vga"). It usually doesn't work on a cold boot, but will on the second or third try.

I have tried
[LIST]
[*]adding the "nomodset" kernel parameter, which made absolutely no change to behavior 
[*]adding the "amdgpu.dc=0" kernel parameter, which made the boot fail every time instead of sometimes 
[*]updating the kernel from "4.15.0-24" to the latest "4.17.4-041704", which made absolutely no change to behavior 
[*]installing the "amdgpu-pro-18.20-606296" driver, which seemed to improve the likelihood of the switch working 
[*]installing the "firmware-amd-graphics" package, which is unavailable but referred to by another package according to apt, despite having non-free sources enabled 
[/LIST]
and those are all the potential solutions to this error I have come across. So far nobody else has reported the sometimes-working behavior either.

Running Kubuntu 18.04 Bionic on a Ryzen 5 2400G.
I also have an RX 480, but that is claimed by the "rd.driver.pre=vfio_pci" kernel option for a virtual machine, and the UEFI is set to use the 2400G (Vega 8) as the default graphics output on boot.
After a successful boot, "lspci" reports the 580 using the vfio-pci driver, and the Vega 8 as using amdgpu.

I have attached the results of running "dmesg -T" immediately after logging in from a successful boot. I have zipped it as the forum refuses to attach 89.6Kb txt, as it is "too large"  :-k
I would attach a log for a failed boot, but given I have no graphical interface at that point, not even a terminal, I don't know how to do that.

---

### Post by oldfred on 2018-07-09
Have you also updated UEFI from motherboard vendor?

        Ryzen 2400G UEFI issue on 4K at 60Hz
[https://ubuntuforums.org/showthread.php?t=2387396](https://ubuntuforums.org/showthread.php?t=2387396)
Raven Ridge With The Ryzen 5 2400G On Mesa 18.2 + Linux 4.17 Is Finally Stable MSI B350M GAMING PRO
[URL="https://www.phoronix.com/scan.php?page=article&item=ryzen-2400g-may&num=1"]https://www.phoronix.com/scan.php?page=article&item=ryzen-2400g-may&num=1
      [/URL]
 Ubuntu 18.04 with updates from ppas
Ryzen 7 2700 / Ryzen 7 2700X / Core i7 8700K Linux Gaming Performance With RX Vega 64, GTX 1080 Ti
[https://www.phoronix.com/scan.php?page=article&item=ryzen-2700-gaming&num=1](https://www.phoronix.com/scan.php?page=article&item=ryzen-2700-gaming&num=1) 
    [URL="https://www.phoronix.com/scan.php?page=article&item=ryzen-2400g-may&num=1"]
[/URL]

---

### Post by &amp;*@Fth&amp;% on 2018-07-09
It appears a bunch of package updates were just pushed to the mainstream repositories, including grub-efi-amd64 and various mesa packages.
Apt reports I now have mesa 18.05 installed after updates, and according to mesa3d.org, 18.2 is not yet released.
I am already on the latest UEFI (released April 4th).
The issue is still persistent.

---

### Post by &amp;*@Fth&amp;% on 2018-07-17
Bump

---

### Post by &amp;*@Fth&amp;% on 2018-08-02
Bump

---

### Post by &amp;*@Fth&amp;% on 2018-08-17
Still a problem, even with all the latest microcode, video drivers, and kernel (4.18.1)

---

### Post by devilsadvocate1987 on 2018-10-05
I'm having the same problem. 

I'm running 18.10 Beta with linux 4.18.0-8, on a Raven Ridge 2400G on the MSI B450M Mortar with the BIOS updated to the latest (7B89v11 with AGESA Code 1.0.0.4C). 18.04 breaks left right and center on Raven Ridge with very strange display tearing issues. I chose not to proceed with trying to poke at 18.04 with a manually upgraded kernel and jumped to 18.10 instead. 

The problem is intermittent when a PCI-express addon card (An ASMedia 4-port (non-RAID) SATA controller) is installed. As far as I can tell, removing the addon card results in a much more reliable boot, to the extent that I would hazard a guess that it almost always boots with no PCI express cards installed. I would have to spend more time with multiple tries to be sure, though, given I've tried a number of combinations and permutations in the last few days in terms of kernels and BIOS versions and settings.

The BIOS update, while dangerous, seems to have generally improved stability. The original BIOS the motherboard came with never booted to linux with the PCI express card installed.  (be prepared to use BIOS+Flashback, and if your motherboard does not support it or something similar to recover DO NOT try it with Linux as the only operating system) 

That said, the most reliable operation I have found so far is :

 - IOMMU enabled in the BIOS
 - "amd_iommu=on" added to /etc/default/grub in GRUB_CMDLINE_DEFAULT
 - both "quiet" and "splash" removed. The splash screen doesn't seem to work anyway.

In addition, I will note that reboot / shutdown both cause a kernel panic when linux does, in fact, boot. 

I will be happy to provide logs or run additional tests on my hardware if needed, let me know if there is a bug open for this thing at Ubuntu or at the kernel. Before I file a bug, though, I do hope to continue to try to work out what exactly the boundary of the problem is. Right now it seems to be all over the place.

---

### Post by oldfred on 2018-10-05
Some other brands, just do not work with Asmedia ports. They standand Intel ports are the only ones that work.
One user only had DVD in Asmedia port and had issues.
But do not know if that applies to newest systems or not.
 Asrock Z170 ASmedia port issue
[https://ubuntuforums.org/showthread.php?t=2345564](https://ubuntuforums.org/showthread.php?t=2345564)

---

### Post by devilsadvocate1987 on 2018-10-06
My bad, it turns out the problem does show up even without the ASMedia SATA port installed. When the system boots, the ASMedia SATA ports work fine, though.

What seems to have more or less stabilized now (and this seems completely independent of whether there's a PCIe card installed or not) : when the boot process attempts to switch from EFI VGA, about a third of the time it boots up fine and everything works. The kernel does still panic when restarting or shutting down with an error about a core being accessed unexpectedly. For a second third, the boot process just sticks there with the text on the screen, the last line being about the switch from EFI VGA, and for the last third,  the screen goes blank at exactly the same point but nothing ever shows up on the screen. I've let it stay there for about 10 minutes for both the last two thirds, so it's not just a longer boot cycle.

This does not seem to depend on whether it's the first boot or not, whether it's a result of a reboot or a full shutdown with power off all the way to the wall. 

I have not seen any noticeable issue on the running operating system when it does boot successfully (until you reboot or shutdown). I have not really stress tested it or tested hibernation. Basic, default sleep seems to be ok.

---

