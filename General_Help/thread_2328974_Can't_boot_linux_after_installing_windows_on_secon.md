---
title: "Can't boot linux after installing windows on second drive"
date: 2016-06-26
forum: General Help
---

### Post by lamda0shotgun on 2016-06-26
So I installed Windows 7 on an additional HDD so I could boot from that when I need to, but apparently I now can't boot from the ubuntu drive as it says something like: Windows couldn't boot, insert correct disk.

So frustrating! I even tried disconnecting the windows drive when booting from the ubuntu one, same message. Did the windows install do something to the motherboard? 

I have testdisk, but have no idea how to use it or what anything it is saying means!

Thanks.

---

### Post by lamda0shotgun on 2016-06-26
Also, sorry if this is not the best place to post, I would appreciate links to more appropriate forums if that would be better.

---

### Post by X-RED_Tech on 2016-06-26
No, Windows did mnothing to the motherboard but it did something to the bootloader, as it always does.
Is it UEFI or BIOS?

---

### Post by lamda0shotgun on 2016-06-26
Efi

---

### Post by X-RED_Tech on 2016-06-26
So Ubuntu was installed in uefi mode and then you also installed Windows 7. Unless you used a USB for Windows 7, its default (installing from DVD) is BIOS with MBR. Assuming BIOS for Windows then you won't be able to dual-boot as usual but you should be able to select what mode to boot with and select the drives independently.

---

### Post by ajgreeny on 2016-06-26
See **Boot-repair** in my signature and follow the instruction in that to run the **Boot-info-script**.

Do not accept the default repair, just run the script and post back here the pastebin link it shows you to enable us to look in detail at what has happened. 

X-RED_Tech has possibly got it right but it will help to see in detail.

---

### Post by grahammechanical on 2016-06-26
I would not be surprised if Windows did not install its boot loader into both hard drives, over-writing the Ubuntu boot loader in the process. The BootInfo summary from boot repair will help us.

Regards.

---

### Post by lamda0shotgun on 2016-06-27
[http://paste.ubuntu.com/17961144/](http://paste.ubuntu.com/17961144/)

---

### Post by grahammechanical on 2016-06-27
You say that you installed windows 7? I do not see it. I see Windows 8 on partition sda3. I see a Windows 7 partition on sda5 but that is a data partition. I do not see any Windows 7 OS files. I see Windows 8 efi boot files in sdb1. The first partition of the second hard drive along with Ubuntu & Zorin efi boot files.

Windows 8 is not listed in the Ubuntu boot loader. I do not think that Windows 7 can be installed in EFI mode but only in legacy mode. I may be wrong on that. The UEFI settings should be looking for an OS to load from the drive with Ubuntu on (sdb). If you can load Ubuntu open a terminal and run this command.

```
sudo update-grub
```

Watch the printout to screen. Does it show a Windows boot loader? If it does you may now be able to load Windows 8. If the UEFI setting utility is looking to sda for an OS then it will not find one there because the boot files (efi) for both Windows & Ubuntu are on sdb.

Regards.

---

### Post by lamda0shotgun on 2016-06-27
Probably because I just upgraded to Windows 10 before running the disk repair! Probably should have mentioned that...

It's also worth mentioning that when I restart my PC the ubuntu drive doesn't come up on the f12 menu, only when I do a pwoer reboot does it appear, and then it's still broken. Nonetheless I can't access my Ubuntu drive whatsoever.

---

### Post by oldfred on 2016-06-27
You are showing Windows on sda and Ubuntu on sdb.
But ESP - efi system partition is sdb1.

Ubuntu's grub only installs to the ESP on sda? Did you swap drives in system? As you do show /efi/ubuntu in ESP on sdb? And you have Windows .efi boot files in sdb1 also.
When you installed Windows to drive that is now sda, was sdb set as default boot in UEFI/BIOS?

You also show sda1 as LDM. That is dynamic partitions with gpt partitioning. Linux used to not see any dynamic partitions, but at least now shows them. The dynamic partitions was a Microsoft logical partitioning system somewhat like Linux LVM - logical volumes as work around to the old MBR 4 primary partition limit. But with gpt I do not see any need for it. Not sure if you can remove it or not. 

With BIOS/MBR and dynamic partitions:
       Dynamic also on gpt as LDM
[http://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv](http://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv) 
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from)

---

### Post by lamda0shotgun on 2016-06-27
Originally I had windows 7 on drive 1, then wiped and tried a couple Linux OS's (zorin) before getting Ubuntu on that same drive, then decided to get Windows 7 on my second 1TB drive, that's where I was when I made this thread. +upgraded windows 7 to 10 now.

The default boot was originally drive1 with windows then linux, but now since getting windows 7 (now windows 10) on my second 1TB drive that automatically started booting by default. 

So what can I do now? Pining for Ubuntu!

---

### Post by oldfred on 2016-06-27
When you plugged in new 1TB drive you used a lower SATA port. Best to have your main booting system in SATA0 and drives in SATA port order. If any DVD have it last.
I have had issues on skipping ports where then flash drive on reboot fills in as that drive number changing all other drives.

Change drive port order so current sdb becomes sda. Then rerun Boot-Repair, perhaps its full un-install/reinstall of grub to make sure you have UEFI NVRAM updated. NVRAM loses its entries when a drive is unplugged. Some find entries on full cold boot or with fast boot in UEFI off, so it searches for new configurations/devices. Or we can use efibootmgr to add entries.

---

