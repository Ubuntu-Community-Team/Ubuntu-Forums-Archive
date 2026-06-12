---
title: "Formatted Ubuntu partition and unable to boot"
date: 2014-12-09
forum: General Help
---

### Post by dave_sl on 2014-12-09
Unfortunately I formatted the Ubuntu disk partition from within Windows 8. After realizing this I tried to restart windows and reinstall Ubuntu from a bootbable USB stick however this failed and my laptop gets stuck at a GRUB screen. It reads:


[SIZE=2][FONT=arial]GNU GRUB version 2.02~beta2-9ubuntu1

Minimal BASH-like line editing is supported. For the first word, TAB list possible command completions. Anywhere else TAB lists possible device or file completions.[/FONT][/SIZE]
[SIZE=2][FONT=arial]
grub>[/FONT][/SIZE]


So I am in the following situation:

[LIST]
[*]The Ubuntu partition has been formatted 
[*]The Windows 8 partition is there and should be functional but I don't know how to boot it from the GRUB command line 
[/LIST]

I'm worried that a stupid mistake has essentially 'bricked' my new laptop... Is it possible to reinstall Ubuntu from the GRUB command line using the USB? Can I boot into Windows from GRUB?

Any suggestions will be really appreciated.

Thanks,
D

---

### Post by oldfred on 2014-12-09
Is this a system with UEFI or pre-installed Windows? If so then you just need to go into UEFI boot and choose to boot Windows. Or one time boot key often f10 or f12.

If you installed and it is BIOS, then you need a Windows boot loader in the MBR. 
You can do that with either your Windows repairCD or flash drive (you did make that?) or from just about any Linux repair system. You can use the Ubuntu live installer and add Boot-Repair or manually install a Windows type boot loader.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
Windows screenshots:
[http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on](http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on)


 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

