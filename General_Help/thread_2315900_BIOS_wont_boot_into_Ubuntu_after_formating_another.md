---
title: "BIOS wont boot into Ubuntu after formating another SSD"
date: 2016-03-03
forum: General Help
---

### Post by andreas52 on 2016-03-03
today i did something dangerous with 2 of my SSDs, i have 2 SSDs lets say SSD "A" and SSD "B"


  SSD A is used by my dekstop computer and runs Ubuntu.

  SSD B is used by my laptop and i wanted to install Ubuntu from  another machine to this SSD and then put it back on the laptop (due to  some problems i had).


  So, my desktop was wotking fine with SSD A running Ubuntu. I switched  off the desktop, i took out the SSD A from the desktops case and  plugged in the SSD B to my desktop. I formated SSD B and installed  Ubuntu using a bootable USB stick. I took out SSD B again and plugged  SSD A back in.


  Now when i try to open the desktop it shows something like a command  line saying "Realtek PXE or something like that" (i guess its a  networking boot) and it says something about DHCP, and thats where it  stucks.
  
I guess that something happend with SSD A and its unmarked from being bootable or something? Can you help me?

Here are some screenshots from the Disks utillity in Ubuntu ( i use it through a live USB stick)   

 
[ATTACH=CONFIG]267616[/ATTACH][ATTACH=CONFIG]267617[/ATTACH]

  Thank you

---

### Post by grahammechanical on 2016-03-03
If SSD A was removed from the desktop case, then whatever you did to SSD B could not have done anything to SSD A. But you may have changed a setting in UEFI that enabled PXE and the machine is now looking to load an OS from a server which it cannot do because a server does not exist and so you get that DCHP message.

Check the settings in the UEFI.

[https://en.wikipedia.org/wiki/Preboot_Execution_Environment](https://en.wikipedia.org/wiki/Preboot_Execution_Environment)

Regards.

---

### Post by oldfred on 2016-03-03
Please attach screen shots. Easy to do with forum's advanced editor and  paperclip icon.
Not everyone has high speed Internet and you can bog their system, just by looking at your thread.

UEFI has NVRAM to remember the entries in UEFI to boot from.
But it forgets everything when you unplug a drive and reverts to defaults. You must have network boot as one of the first boot options, if drive not found.

You may need to boot, full cold power boot, not warm reboot and UEFI may find entries in ESP - efi system partition.
Or you may have to add entries again with efibootmgr or by a full reinstall of grub which also runs the efibootmgr commands.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Boot-Repairs advanced mode has the full uninstall/reinstall of grub.

---

### Post by andreas52 on 2016-03-03
> **oldfred said:**
> Please attach screen shots. Easy to do with forum's advanced editor and  paperclip icon.
Not everyone has high speed Internet and you can bog their system, just by looking at your thread.


I corrected it, thank you for the notice!

> **oldfred said:**
> Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)


Here you go. Note that i now have plugged in to the desktop SSD A and SSD B and i booted Ubuntu from SSD B. I need to be able to remove SSD B and boot from SSD A

[http://paste.ubuntu.com/15274025/](http://paste.ubuntu.com/15274025/) 

> **oldfred said:**
> You may need to boot, full cold power boot, not warm reboot and UEFI may find entries in ESP - efi system partition.


I didnt understand any of this :/

---

### Post by oldfred on 2016-03-03
You have two totally different types of installs.
Your sda is UEFI with gpt partitions.
Your sdb is BIOS with MBR partitions.

With UEFI, the boot flag must only be on the FAT32 partition. It is not really the same as a BIOS boot flag as with gpt it is setting a very long GUID, so UEFI knows to look for boot files. Use gparted and move boot flag from sda2 to sda1.

Even with BIOS grub does not use boot flag. A very few BIOS need to see a boot flag, so we still suggest one. They must assume systems are only Windows as Windows does have to have a boot flag on the primary NTFS partition with more Windows boot files.
Lilo and Syslinux also do use boot flag.

After you move boot flag, you may still have to go into UEFI/BIOS and turn on/off UEFI boot or CSM/Legacy/BIOS boot mode to boot drive with system installed in that mode.

Do not run any auto fix with Boot-Repair.
You want UEFI repairs on sda and BIOS repairs on sdb. You should boot live installer in mode you want to repair, but Boot-Repair can do things in advanced mode if you specifically tell it.

Is other system for sdb drive UEFI or BIOS only?

---

### Post by andreas52 on 2016-03-03
> **oldfred said:**
> 
Do not run any auto fix with Boot-Repair.
You want UEFI repairs on sda and BIOS repairs on sdb. You should boot live installer in mode you want to repair, but Boot-Repair can do things in advanced mode if you specifically tell it.

Is other system for sdb drive UEFI or BIOS only?

Both systems (my desktop and laptop) support UEFI and BIOS if you mean that. I used gparted and moved boot flag from sda2 to sda1 as you said.

---

### Post by oldfred on 2016-03-03
From UEFI boot menu in UEFI mode can you now boot sda?

Often better to use UEFI and also better even if BIOS and only Ubuntu to use gpt partitioning. 
Ubuntu can boot from gpt with UEFI or BIOS, but UEFI needs ESP - efi system partition or BIOS needs bios_grub. 
When I partition a new drive I always add both an ESP and bios_grub partition as first two partitions. Then I can install in either mode or later easily change as adding partitions at beginning of drive or changing from MBR to gpt when drive is full of data can be very difficult.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

---

### Post by andreas52 on 2016-03-03
Problem solved! :D i dont know how to thank you enough!

It seems that my BIOS had an option at the Boot tab saying OS type: and it was saying Windows UEFI, i changed it to Other OS and also added UEFI to the previous lists,

Thank you so much, have a great day!

---

### Post by oldfred on 2016-03-03
I believe the Windows and "Other" is really UEFI Secure boot or just UEFI boot. 
That is how my motherboard works.

If UEFI Secure boot is on, only systems installed with Secure boot will work.
If Secure boot is off, then UEFI or BIOS will work. And you should get both options in UEFI boot menu.

---

### Post by oldos2er on 2016-03-03
Moved to General Help.

---

