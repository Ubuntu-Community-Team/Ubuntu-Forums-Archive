---
title: "Cannot boot Ubuntu after adding 2nd hard disk"
date: 2013-11-29
forum: General Help
---

### Post by ofnuts on 2013-11-29
My family PC dual-boots Kubuntu 10.04 and WinXP. The MB used to be a MSI but I recently replaced it with a Gigabyte one (Z77-DS3H)(and a new video card). No problem booting XP or Kubuntu with that setup. 

To this I just added a new (unformatted) hard disk (Seagate barracuda 2TB SATA). On startup I see the grub menu, I can even boot the WinXP, but booting Linux (the two available kernels, in standard or recovery mode) leads to a dark screen (and there doesn't seem to be much disk activity).

What can be going wrong? What log file should I recover on the hard disk if I boot a CD?

---

### Post by fantab on 2013-11-29
Try booting with 'NOMODESET' during boot. Sounds like a graphics issue to me.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Also, its time you moved on from both Kubuntu 10.04 and XP. Both are dead. No more support.
There newer versions deal better with newer hardware.

---

### Post by ofnuts on 2013-11-29
The reason for the new disk is to receive a more recent Ubuntu and Win7, but I want the transition to go smoothly and keep XP until I'm sure Win7 does everything it did (transfer important apps, etc...)..

Edit: I wonder about the graphics issue because I had no problem with that same mobo/gfx cards combo before adding the new HDD.

I can of course install a more recent Kubuntu+Grub on the new disk (that was in plan), but that makes me wonder if Win7 will wipe it out when I will install it (so I planed to install Kubuntu after Win7). How will the BIOS determine which HDD to boot on (and so which grub instanc is used? Is it a matter of SAT connector in the MB? I couls see a boot order option in the BIOS but it seemed to be optical drives vs some generic HDD, and I didn't find anything that looked like the choice betweeh the two HDDs.

---

### Post by oldfred on 2013-11-29
Your motherboard is new enough to be UEFI with BIOS as CSM.
       UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

How you boot installer is how it installs or if you boot either Windows or Ubuntu in UEFI mode it will install in UEFI mode. Or if booted in BIOS mode it will install in BIOS mode. I think Windows 7 DVD is BIOS only and needs to be copied to a flash drive and some minor updates to make it UEFI compatible.

However you install you want both systems in same boot mode, both BIOS or both UEFI.

Also with new drives you should be in AHCI mode, but older XP installs do not have AHCI drivers. It really requires a new install of XP, so I decided to shutdown XP (yea, no Windows) when I got a new SSD that needed AHCI for trim to work.

Boot drive is always hd0 in grub as defined by BIOS, but drives will be in port order from motherboard. I skipped a port and now if I plug in a flash drive it is sde, but if I reboot it is sdb and all higher number drives get changed. With UUIDs everything works, but I have to be careful if running some command on device like /dev/sdd, which drive is really sdd?

What video card? And is is dual video? As motherboard may also output Intel video.

I am not using Windows anymore, but still prefer to have Windows on one drive and Linux on all my other drives.

---

### Post by ofnuts on 2013-11-30
Ubuntu and WinXP were installed in a former life of the system (4-5years old, so no UEFI). Changed MB+GFX (Nvidia GTX660) two onths ago, and both opsys booted without problems (upgraded the GFX driver on Windows). The Linux dark screen came when the only change was the added HDD, which appears to be seen as HDD #2 sincei I get the Grub screen. But from that boot screen I can boot WinXP (works without problems, and  sees the new HDD as unformatted) but Linux doesn't start.

---

### Post by oldfred on 2013-11-30
With my nVidia card screen goes black or monitor turns off, but system is still booting. I have to have nomodeset on grub linux line until I install the nVidia proprietary drivers.

---

