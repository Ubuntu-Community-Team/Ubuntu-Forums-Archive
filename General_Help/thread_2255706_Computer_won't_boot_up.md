---
title: "Computer won't boot up"
date: 2014-12-06
forum: General Help
---

### Post by hayden6 on 2014-12-06
:icon_frown:Thank you so much for clicking on this,my computer was duel booted with Ubuntu and windows 8 ,in windows 8 i was trying to uninstall Ubuntu and deleted partitions that  i am not so sure anymore were Ubuntu it was fine then when i restarted my computer could never get it back on. when it loads up it says     

error: no such device: 7377df0a-49c5-4c4b-9b64-dec6e9c7870c .
Entering rescue mode...
grub rescue> 


i really need help its fine if it takes a week to do i just want my computer back. :cry:

---

### Post by oldfred on 2014-12-06
If you had Windows 8 pre-installed then you have UEFI. And UEFI controls booting. You should just be able to go into UEFI and set Windows as first in Boot order. Or use one time boot key like f10 or f12, but that varies by vendor.

If that does not work post link to summary report. Boot-Repair cannot fix most Windows issues and occassionly makes it worse. So do not run auto fix until someone has reviewed your summary report.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by hayden6 on 2014-12-06
i did not have it preinstalled i built my computor.ALSO what do i link it to i cant get on my computor at all im using my laptop?

---

### Post by oldfred on 2014-12-06
Use live installer flash drive. You install Boot-Repair into live installer and upload from it.

If you installed in BIOS boot mode on MBR(msdos) partitioned drive, you just need to install a Windows boot loader to the MBR. You can use Boot-Repair for that, or your Window installer or a Windows repairCD or flash drive. 

 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

You did make this when Windows was working, so when it breaks you can fix it?

 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

