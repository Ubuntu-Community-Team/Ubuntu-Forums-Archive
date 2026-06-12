---
title: "Uninstall Ubuntu on dual boot machine"
date: 2015-06-30
forum: General Help
---

### Post by jminor2 on 2015-06-30
Hello,  I currently have Windows 7 and Ubuntu installed on a laptop.  I would like to uninstall ubuntu and just run windows.  I purchased another laptop to run ubuntu alone.  Can I just uninstall Ubuntu, or do I have to re install Windows?

Thanks,

John

---

### Post by oldfred on 2015-06-30
Is Windows UEFI or BIOS?
Most Windows 7 systems are BIOS, but a few are UEFI.

You need to make sure you can boot Windows directly before removing Ubuntu partition. 
If BIOS the grub boot loader in the MBR has to load more boot files & grub menu from Ubuntu partition. If you delete partition first, you just get grub> and no boot.

Best to also have a Windows repairCD or flash drive. Many Windows repairs cannot be done from Linux.
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
      
 Restore MBR for win7
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

    Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by jminor2 on 2015-06-30
When I start my machine, I get a window where I select either Ubuntu or Windows to start up.  So I would imagine I have to run the Windows repair/recovery usb.
Thanks for your help.
John

---

