---
title: "Grub only boots Ubuntu if I reboot"
date: 2020-12-01
forum: General Help
---

### Post by tremon36 on 2020-12-01
Hello there! This is my first post in this forum.
Normally, I find a lot of information here to solve my problems with the OS, but I couldn't find any solution to this one, so I'm posting this to find someone who has any idea of what is happening to my computer.

I have Ubuntu on dual boot with windows (Grub 2 bootloader). It all worked fine until one day, I accidentally disconnected my computer from power, and after that, this has been happening:

Ubuntu won't boot at first when I turn on the computer.
If I boot into windows, wait some time and reboot,then boot ubuntu, it boots and runs just fine.
If I boot into recovery mode, I can boot ubuntu from there, and it works OK (without the graphic drivers). Again, if I wait some time and then reboot to ubuntu, ubuntu boots and works perfectly.
However:
- if I reboot too early, it doesn't work (in both cases)
- if I shut down the computer for a long time (more than an hour or so) it doesn't boot again- if after using windows for some time I shut down the computer for a little period of time (some minutes) ubuntu will boot perfectly fine
- Windows always boots perfectly

I suspect it is a grub 2 problem, as I have reinstalled ubuntu and nothing changes.
Do you have any ideas on how to solve this? Thanks!

---

### Post by oldfred on 2020-12-01
Double check UEFI settings.
Have you updated firmware for UEFI?
What brand/model system?
What video card/chip?

This may not show anything, but then we can rule out grub configuration issues.
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repa](https://help.ubuntu.com/community/Boot-Repa)

---

### Post by tremon36 on 2020-12-02
Hello. I don't know what that UEFI settings are.
In bios there are some options, I have set all of them to "UEFI ONLY"
I don't think I have installed any firmware for UEFI (sorry for my ignorance about UEFI&#55357;&#56837;)
I have a b450 Aorus motherboard, ryzen 5 3600 processorRadeon rx480 vídeo card.
Here is the boot info summary (I did it in a live session with the installer USB) [https://paste.ubuntu.com/p/jSWY6xbDMY/](https://paste.ubuntu.com/p/jSWY6xbDMY/)
thank you for your answer :)

---

### Post by CelticWarrior on 2020-12-02
UEFI is what replaced BIOS a long time ago but some manufacturers and many people, both engineers and laypersons, still call it "BIOS". So, UEFI settings means "BIOS" settings. And double check UEFI settings in the context of this thread probably means - I'm not trying to read oldfred's mind - to check whether Fast Boot is disabled (not mentioned in the summary report), Secure Boot is disabled (OK, it is) and the boot order (it still points to Ubuntu-Grub, so it should be fine.

Furthermore, UEFI *is* the firmware, just like BIOS was a decade ago. And you should update it if the motherboard's vendor has an update released.

I would also recommend disabling Fast Startup in Windows as it sometimes interferes - it shouldn't but sometimes it does - with the ESP (EFI System Partition) where the bootloaders are.

---

### Post by tremon36 on 2020-12-02
Okay, here are the UEFI/BIOS settings:
Boot option priorities:
Boot Option #1.     Ubuntu (P0: Toshiba DT01ACA 100)
Boot Option #2.     Windows Boot Manager (P0: Toshiba DT01ACA 100)
Boot Option #3.     P0: Toshiba DT01ACA 100Boot Option #4.     Realtek PXE BE D00

Boot up NumLock State.      ON
Security Option.                    System
Full Screen LOGO Show.      Enabled

Fast boot.                             Disabled

CSM support.                                Enabled
LAN PXE boot option ROM.           Enabled
Storage Boot Option control.         UEFI only
Other PCI device ROM priority.      UEFI only

I'm out of ideas of what to do, this is something really weird

---

### Post by CelticWarrior on 2020-12-02
Not that it would make much of a difference but
```
[COLOR=#000000]CSM support. Enabled[/COLOR]
```
can, theoretically, confuse things when booting. CSM = Legacy mode = "BIOS" mode. With all OSes installed in UEFI mode (as they should be) there's no point in keeping CSM enabled. Disabling it may improve boot time.

---

### Post by oldfred on 2020-12-02
You have UEFI system.
And Ubuntu is now installed in UEFI boot mode as you have mount of the ESP - efi system partition in fstab.

But you have at some point installed grub in BIOS boot mode as you have grub in gpt's protective MBR for BIOS boot.
So that may be part of issue.
System may in BIOS/Legacy/CSM mode see grub for BIOS boot and try to boot. But that will fail as grub is now set for UEFI boot.
Just do not try to do anything in BIOS mode, as it will not work.

Some issues seem consistent by brand and some by model/version.

Not sure if these provide any additional info or not.
Asrock B450 UEFI & Driver update to stop flickering.
[https://pcpartpicker.com/b/t4KBD3](https://pcpartpicker.com/b/t4KBD3)
Asrock B450M Steel Legend - turn UEFI Secure Boot off
[https://askubuntu.com/questions/1183093/ubuntu-corrupts-bios-on-ryzen-3000-machine](https://askubuntu.com/questions/1183093/ubuntu-corrupts-bios-on-ryzen-3000-machine)
MSI B450 Tomahawk Max & MSI Nvidia GTX 1080 TI UEFI update & defaults
[https://ubuntuforums.org/showthread.php?t=2450961](https://ubuntuforums.org/showthread.php?t=2450961)
Asus B450-F Clock speeds
[https://ubuntuforums.org/showthread.php?t=2414502&p=13845363#post13845363](https://ubuntuforums.org/showthread.php?t=2414502&p=13845363#post13845363)


These are now older, so newer version of Ubuntu has newer drivers. 
Gigabyte B450 Ryzen needs kernel & mesa drivers
[https://ubuntuforums.org/showthread.php?t=2408247](https://ubuntuforums.org/showthread.php?t=2408247) & 
[https://ubuntuforums.org/showthread.php?t=2423649](https://ubuntuforums.org/showthread.php?t=2423649)

---

### Post by tremon36 on 2020-12-04
After trying everything, I decided to reinstall windows and Ubuntu, deleting all partitions first (clean install). However, the problem still persists, so I think this is a bios problem, or maybe a hard drive problem. I think my bios was updated recently, as there are some options I have never seen... But I didn't manually install anything, so idk. Maybe there is the problem

---

### Post by oldfred on 2020-12-04
Did you reinstall in UEFI boot mode to gpt partitioned drive?

Just to confirm install configuration:
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by andrewr23 on 2020-12-07
> After trying everything, I decided to reinstall windows and Ubuntu, deleting all partitions first (clean install). However, the problem still persists, so I think this is a bios problem, or maybe a hard drive problem. I think my bios was updated recently, as there are some options I have never seen... But I didn't manually install anything, so idk. Maybe there is the problem like in the [COLOR=#1155CC][FONT=Arial][https://college-homework-help.org/blog/fastest-growing-careers](https://college-homework-help.org/blog/fastest-growing-careers)[/FONT][/COLOR]
so basically you are saying that this is an hardware problem?

---

