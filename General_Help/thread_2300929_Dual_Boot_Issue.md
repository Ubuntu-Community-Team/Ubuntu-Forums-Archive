---
title: "Dual Boot Issue"
date: 2015-10-29
forum: General Help
---

### Post by kalantos on 2015-10-29
Hi guys! yesterday i installed ubuntu in my laptop (it has windows 10), but i think i installed ubuntu loader over windows loader, so when GRUB comes up it gives me the option of windows or ubuntu but when i choose windows it takes me to ubuntu. any solution?
Thanks!;)

---

### Post by leunam12 on 2015-10-29
repeated by mistake

---

### Post by leunam12 on 2015-10-29
Open terminal and type the following commands pressing enter after each line.
```
sudo grub-install /dev/sda
sudo update-grub
```

(I am assuming that you only have one hard drive and it is sda. If you are not sure post the results of lsblk before you run the commands)

---

### Post by kalantos on 2015-10-29
here are my partitons
[ATTACH=CONFIG]265237[/ATTACH]

thanks for answering so quickly :D

---

### Post by sandyd on 2015-10-29
> **kalantos said:**
> here are my partitons
[ATTACH=CONFIG]265237[/ATTACH]

thanks for answering so quickly :D

Yep, you only have one drive.

Edit: Replaced large image with thumbnail for people with slower internet

---

### Post by oldfred on 2015-10-29
Did you leave Windows 10 hibernated or what it calls fast start up?

       Fast Startup off
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
More explanation of NTFS driver & Windows hibernation
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

If so, you may need to temporarily reinstall the Windows boot loader and boot into Windows. F8 may be required to run Windows repairs. Once you have Windows booting ok, then restore grub2 boot loader to MBR. Grub only boots working Windows so best to always have a separate Windows repair CD or flash drive.

BIOS boot of Windows is now the same for all versions after XP.
      
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

           
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by leunam12 on 2015-10-30
try the commands posted above (sda is the right drive). If it doesn't work try boot-repair, if it doesn't work you have to boot to your Windows recovery partition or from installation media to do the repairs there.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

