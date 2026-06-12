---
title: "[Ubuntu/Windows 8] Grub Rescue"
date: 2014-08-13
forum: General Help
---

### Post by aniqpirzada on 2014-08-13
Hi,
firstly im using a old laptop with broken keys so sorry for typo's etc.

anyway i used to have ubuntu + windows 8 but since my windows HDD space was only 15gb left, i used a application called easeUS partition manager to allocate the ubuntu HDD to windows8.
After the process completed and laptop restarted i was left hanging on this screen:
```
error: unknown filesystem
entering rescue mode...
grub rescue>
```

i researched online and it said i have to recover the windows boot loader so i had a old windows vista cd which i put in and tried to boot from it but the grub loader still came up.
i do not know how to remove it.


at the moment im dowloaidng ubuntu again so i can try and make a live usb and try to fix it using that.
but if anyone else can help me that would be great.

i do not really need ubuntu anymore so if you can help me get rid of the grub boot loader that would be helpful


thannks

---

### Post by oldfred on 2014-08-13
Do not reinstall Ubuntu as that may erase entire drive, unless you use Something Else to install.

You should be able to use a Windows repair flash drive.
I think this works whether UEFI or BIOS.
       Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

Since it sounds like an older system it should be BIOS not the new UEFI that pre-installed Windows 8 systems have.
      
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by aniqpirzada on 2014-08-13
do you know where i can download windows 8 iso.

---

### Post by oldfred on 2014-08-13
If your PC did not come with a complete Windowsinstallation CD, you can download a Repair Disc at the following links (Now $20 to $40), of course you can make one for free from a working install:
       
 Windows 8 repair Disc - for repairs only
[https://neosmart.net/blog/2012/windows-8-recovery-disk-download/](https://neosmart.net/blog/2012/windows-8-recovery-disk-download/)

Probably better to just purchase a new full copy of Windows, if you need a new one.

If you have access to another working Windows 8:
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

