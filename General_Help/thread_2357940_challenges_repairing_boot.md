---
title: "challenges repairing boot"
date: 2017-04-07
forum: General Help
---

### Post by rwelty1889 on 2017-04-07
i'm new to this forum but a long time linux user, i'm working on helping a friend repair a boot problem on his 16.04 system (an HP Pavilion).

currently if we try to boot from the hard drive, we get this message

       ERROR: No boot disk has been detected or the disk has failed.

He installed a boot repair image on a USB drive and we have started it up. it scans the hard drive and reports

   /boot detected. Please check the options.

Recommended repair produces the (apparently rather common) message
 
   GPT detected. Please create a BIOS-BOOT partition...

we have yet to figure out the correct way past this problem.

Boot-Info shows "=> No boot loader is installed in the MBR of /dev/sda"

so clearly we need to reinstall Grub in the MBR, but some sort of UEFI issue is interfering with this. the forum answers to this point haven't really yielded the answers we're looking for.

we have copied Boot-Info to [http://paste.ubuntu.com/24335401/](http://paste.ubuntu.com/24335401/)

thanks in advance for your help,
   richard

---

### Post by oldfred on 2017-04-07
You have an UEFI system.
But HP is not UEFI boot friendly to anything other than Windows.
It violates UEFI standard that says NOT to use description as part of boot. And "Windows Boot Manager" is only valid description.
Multiple work arounds, but if only Ubuntu you can make description to boot Ubuntu be "Windows Boot Manager". It does not check actual boot file is not the Windows one.

Boot-Repair asking for bios_grub partition is trying to do a BIOS boot fix on gpt partitioned drive.

You also show ESP - efi system partition as FAT16. While allowed, that was really only for external drives. Should be FAT32 and best to fix now. May be why Boot-Repair says you do not have ESP as it expects FAT32 formatted partition with boot flag.

Use parted, gparted, gdisk or your favorite partitioning tool and convert sda1 to FAT32.
Use Boot-Repair and run the full uninstall/reinstall of grub2. Be sure to unencrypt the LVM if encrypted. Boot-Repair may not ask for that. It has issues knowing if LVM or RAID as both use /mapper.

Also check this in Boot-Repair.
In Boot-Repair "Use the standard EFI file" Should do the same as these  manual instrutions by copying shimx64.efi to /EFI/Boot/bootx64.efi for  fallback or hard drive  boot from UEFI menu.

Boot-Repair should make or copy shimx64.efi to /EFI/Boot/bootx64.efi. That is a fallback or hard drive boot entry that UEFI does support.
You then should be able to boot the hard drive or the Windows entry.

# You may need new hard drive entry (uses default  of sda1 for ESP):
 sudo efibootmgr -c -L "UEFI Hard drive" -l "\EFI\Boot\bootx64.efi"

Use efibootmgr, if only Ubuntu install, not dual boot, install to make  Windows UEFI description boot grub or shim file (Assumes default of sda1  for ESP, see links for added parameters for different drive or  partitions):
         sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

More details in link in my  signature.

I believe these users manually copied files into /EFI/Boot as then Boot-Repair did not do it.
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)

---

### Post by rwelty1889 on 2017-04-15
we have recovered the system. i suspect that we may have been looking at different version of things as the process did not precisely match what you outlined; but it contained the information we needed to straighten it out.

we didn't succeed in converting the FAT16 partition to FAT32. gpartd give us the option but it didn't seem to work properly, it was very strange.

boot-repair did not give us a [COLOR=#000000]"Use the standard EFI file" option.

i located a [/COLOR][COLOR=#000000]grubx64.efi file that looked like the right one, copied it into /EFI/Boot/bootx64.efi and that did the trick. after that, boot-repair was able to execute the normal repair option and the system came back.

thanks for you help,
   richard[/COLOR]

---

