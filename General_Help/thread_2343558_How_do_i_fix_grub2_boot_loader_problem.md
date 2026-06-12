---
title: "How do i fix grub2 boot loader problem?"
date: 2016-11-17
forum: General Help
---

### Post by manojkl on 2016-11-17
[COLOR=#111111][FONT=Ubuntu]I have recently dual booted windows with ubuntu. I have HP Pavilion 15-n003tx model with me. My issue is that I have not been able to get it to boot straight off the new efi file that was created. So i did this solution [/FONT][/COLOR][http://askubuntu.com/a/381741/620153](http://askubuntu.com/a/381741/620153)[COLOR=#111111][FONT=Ubuntu] After this i am not able to login to windows using windows boot manager since this links to the same .efi file. Any help regarding this ?. I also got one solution described in [/FONT][/COLOR][http://askubuntu.com/a/496840/620153](http://askubuntu.com/a/496840/620153)[COLOR=#111111][FONT=Ubuntu]. As i am new to ubuntu not able to understand the solution. Any help is much appreciated[/FONT][/COLOR]

---

### Post by oldfred on 2016-11-17
Your first solution was one that used to be used, as some of the other work arounds were not known.
But as you found, you cannot then directly boot Windows from UEFI, only from grub. And then if Windows has any issues grub will not boot it.

Some HP have a UEFI setting buried pretty deep that will let you configure to boot Ubuntu directly.
       HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216)

You do want to make sure that /efi/Microsoft/Boot/bootmgfw.efi is the Windows copy, not anything else.

Most with HP use the fallback or hard drive boot entry. Systems boot from /EFI/Boot/bootx64.efi. That is the file that all external drives use (whether Windows installer or Ubuntu installer) and is now also available in internal hard drives with UEFI. We copy shimx64.efi to be bootx64.efi and if UEFI already has a UEFI hard drive or fallback entry it will boot Ubuntu. Some have to add the UEFI entry to use bootx64.efi.

Boot-Repair now can do the copy so you do not have to manually copy it.
      
 **A:** Manually rename files efi boot files in efi partition

 **a1**: Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry in UEFI menu like this:
Boot0013* UEFI OS	HD(1,800,fa000,3195d314-ce88-42ac-beac-d9f80289ac11)File(\EFI\BOOT\BOOTX64.EFI)..BO
Boot-Repair now creates  bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI.
'Use the standard EFI file' in advanced options.
[URL="https://bugs.launchpad.net/boot-repair/+bug/1531178"]https://bugs.launchpad.net/boot-repair/+bug/1531178

      [/URL] Copy to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
Rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019) 
    
Older threads with HP where users manually copied files.
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 

[URL="https://bugs.launchpad.net/boot-repair/+bug/1531178"]
[/URL]

---

