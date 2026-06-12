---
title: "Fixing Grub loader"
date: 2014-10-03
forum: General Help
---

### Post by Giorgos_Paralikidi on 2014-10-03
[FONT=arial]Hello,
I have a laptop running Windows 8 and Ubuntu (dual boot). Today Ubuntu asked to install a major update and after completing that update the entry "Windows UEFI" does not appear on the GRUB boot list. I can not only boot Ubuntu!

I tried to use Boot Repair over a live CD to perform a recommended fix but I had no luck! Although when I start the program it says that "EFI detected"
I was reluctant to change the advanced options to apply possible fixes, because I was not so confident that this was the correct thing to do, However I produced the log that may be of help and it is on this link:

[/FONT]http://paste.ubuntu.com/8488497/

My question is how to make the Windows UEFI entry come up in the boot list of Grub!

Thanks for your help in advance!
George

---

### Post by moe7 on 2014-10-03
hello there ...

i had the same problem before i think you only need to update ur grub when u are on ubuntu and it will fix the problem

---

### Post by Giorgos_Paralikidi on 2014-10-03
I have already tried to update Grub from terminal in Ubuntu but didn't help. The same problem!

---

### Post by grahammechanical on 2014-10-03
Could you please explain your hard disk and partition layout. Boot Repair detects 5 partitions on sdc. Where are sda and sdb? First hard disk = sda. Second hard disk = sdb. third hard disk = sdc.

Another thing. Windows 8 is shown on sdc partition 3 and 4 but where are the Windows 8 boot files (Windows 8 boot loader) and the Windows 8 executable? 

What are isw_gaehiiagi_Volume11 to Volume 14?

When an update/upgrade includes a kernel upgrade, then the Grub configuration files get re-written and Grub gets re-installed and that is by default in sda. But in order to put Windows 8 into the Grub boot menu Grub OS-prober utility needs to find a Windows 8 boot loader. And it cannot do that.

It seems that sda and sdb are set up as RAID and that is where the Windows 8 boot files are.

> [COLOR=#BB4444]Presence of EFI/Microsoft file detected: /mnt/boot-sav/mapper/isw_gaehiiagi_Volume1p2/EFI/Microsoft/Boot/bkpbootmgfw.efi[/COLOR]
[COLOR=#BB4444]Presence of EFI/Microsoft file detected: /mnt/boot-sav/mapper/isw_gaehiiagi_Volume1p2/EFI/Microsoft/Boot/bootmgfw.efi[/COLOR]
[COLOR=#BB4444]Presence of EFI/Microsoft file detected: /mnt/boot-sav/mapper/isw_gaehiiagi_Volume1p2/EFI/Microsoft/Boot/bootx64.efi[/COLOR]
[COLOR=#BB4444]Presence of EFI/Boot file detected: /mnt/boot-sav/mapper/isw_gaehiiagi_Volume1p2/EFI/Boot/bkpbootx64.efi[/COLOR]
[COLOR=#BB4444]Presence of EFI/Boot file detected: /mnt/boot-sav/mapper/isw_gaehiiagi_Volume1p2/EFI/Boot/bootx64.efi[/COLOR]
[COLOR=#BB4444]Presence of .bkp file detected: /mnt/boot-sav/mapper/isw_gaehiiagi_Volume1p2/EFI/Boot/bkpbootx64.efi[/COLOR]
[COLOR=#BB4444]Presence of .bkp file detected: /mnt/boot-sav/mapper/isw_gaehiiagi_Volume1p2/EFI/Microsoft/Boot/bkpbootmgfw.efi[/COLOR]

You did not accept the recommended repair

> Recommended-Repair
This setting would purge [COLOR=#666666]([/COLOR]in order to fix packages sign-grub [COLOR=#AA22FF]enable[/COLOR]-raid fix executable upgrade version[COLOR=#666666])[/COLOR] and reinstall the grub-efi-amd64-signed of sdc1, using the following options: upgrade-grub       mapper/isw_gaehiiagi_Volume1p2/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot




And so nothing was changed
> 
[COLOR=#666666]===================[/COLOR] Settings chosen by the user
Boot-Info
This setting will not act on the MBR.

No change has been performed on your computer.

It is your computer. It is your choice. You can run Boot Repair again and this time accept the recommend repair and may be fix things. Or not.

Regards.

---

### Post by Giorgos_Paralikidi on 2014-10-03
Hello grahammechanical and thank you the time you spend on reviewing my problem.

Here is my situation with the disks:
The computer has a total of 3 disks, 2 x 128GB SSD and 1 x 1000GB HDD. The 2 SSDs are set in Raid0, so from the Windows OS I can see them as onen disk of a little bit less than 256GB. That is where Windows are installed from the time I bought the computer.
The 1000GB disk was partitioned in 5 parts, 1 for Ubuntu, 1 for Swap, and 3 others.

I re-run the Boot-Repair tool to do the recommended repair, since I must have done something wrong to not accept it the previous time. That did not help. Here is the new log file: [http://paste.ubuntu.com/8489243/](http://paste.ubuntu.com/8489243/).
Sorry for not being too helpful but I really don't have a clue what the isw_gaehiiagi_Volume11 to Volume 14 are.

Is there a way to explicitily state that I want the boot files that exist in sda and sdb to be used?

---

### Post by oldfred on 2014-10-04
I also am still confused. Were you able to boot Windows from grub menu or just from f12, f10 or whatever one time boot key is?

UEFI and BIOS installs are not compatible, once you start booting in one mode you cannot switch, so if Ubuntu is in BIOS boot mode in sdc, it cannot boot Windows in UEFI mode. You have to reboot into UEFI. Some auto switch and others require you to turn on/off UEFI or BIOS/CSM boot modes.

And Ubuntu desktop does not normally include the RAID drivers, you have to add those, which Boot-Repair does to see the /mapper partitions.

Your sdc is a MBR(msdos) partitioned drive so you can only boot it in BIOS mode. 
UEFI requires gpt partitioning with an efi partition formatted FAT32 with the boot flag. 
Although the Ubuntu installer does use MBR but that is FAT32 with both syslinux for BIOS and efi boot files for UEFI all in one partition.

---

