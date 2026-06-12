---
title: "I've made a mess... grub issues."
date: 2017-10-11
forum: General Help
---

### Post by Mazate on 2017-10-11
Hi there, sorry for the boring back story but I'm afraid that it's necessary to explain my current predicament.

I've been using two hard drives on my computer, on with windows 10 and one with mint.  The primary hard drive in the boot order was the one with windows on it.  Apparently, and I could be wrong, grub was installed on the windows disk.  Whenever I started my computer I was asked which one I wanted to load and it always worked fine.  Fast forward to about 30 minutes ago.  I decided that I wanted to install Ubuntu 17.10 in place of mint.  To ensure that I didn't mess up my windows HD, I disconnected it from the motherboard temporarily while I wiped the other HD and installed 17.10 over it.  The hard drive with 17.10 on it works just fine (As an aside, it looks very nice with gnome).  Anyway, I went to plug the windows HD back into the motherboard and restarted the computer.  Since the winidows HD is the master, it loads first.  The problem I have now is instead of grub loading to ask me which one I want to load, I get a page that says:

> error: no such device:  xxxx-xxxx-xxxx
Entering rescue mode...
grub rescue>

And it sits there with a prompt.  I'm sure that I screwed things up by doing the install with the other hard drive unplugged.  I did that because my motherboard never sees both drives for some reason.  It sees one or the other.

Anyway, if anyone knows of a solution to my current situation, I would be most appreciative if you would be kind enough to share it with me.

---

### Post by khoriam on 2017-10-11
Try boot-repair or fix boot with live windows cd (helped me when I removed the whole efi/boot partition).

---

### Post by Mazate on 2017-10-11
Unfortunately I don't have a windows CD.  Would boot-repair require one?

---

### Post by khoriam on 2017-10-11
Nah, boot-repair would not.

---

### Post by oldfred on 2017-10-11
UEFI or BIOS?

If UEFI you just need to use one time UEFI boot key and boot Windows. And you can change boot order in UEFI. Or use efibootmgr in Linux to change UEFI boot order.

If BIOS, then Boot-Repair can only do a few minor things. But it can install a Windows type boot loader as long as it can see Windows or it is not hibernated nor fast start up on.

Whether BIOS or UEFI, you should make the Windows recovery flash drive as soon as you can boot.
Always have a repair flash drive for every system you have installed. The Ubuntu live installer works for Linux when in live mode.

       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

You can post the link from Boot-repair's Summary Report if not working. But Windows may need its repair disk.

---

### Post by khoriam on 2017-10-11
> **oldfred said:**
> UEFI or BIOS?

If UEFI you just need to use one time UEFI boot key and boot Windows. And you can change boot order in UEFI. Or use efibootmgr in Linux to change UEFI boot order.

If BIOS, then Boot-Repair can only do a few minor things. But it can install a Windows type boot loader as long as it can see Windows or it is not hibernated nor fast start up on.

Whether BIOS or UEFI, you should make the Windows recovery flash drive as soon as you can boot.
Always have a repair flash drive for every system you have installed. The Ubuntu live installer works for Linux when in live mode.

       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

You can post the link from Boot-repair's Summary Report if not working. But Windows may need its repair disk.

I guess, windows will surely need the repair disk due to its locationon the separate drive.

---

### Post by oldfred on 2017-10-11
Post link to Summary Report, so we can see exact configuration.

Whether separate drive or not does not matter much, but whether UEFI or BIOS has huge differences in configuration.

You can make a repair/recovery drive from any Windows 10 system.
       Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by Mazate on 2017-10-11
Given that windows won't boot up I think my opportunity of creating a repair/recovery CD has probably passed.

---

### Post by oldfred on 2017-10-12
Do you have access to another Windows 10 system from school, work or a friend.

Technically you can download the full Windows 10 installer and use it for 30 days before you have to pay for it again. It may have the repair console as part of it, but I have never used it.

       How to: perform a repair upgrade using the Windows 10 ISO file
[http://answers.microsoft.com/en-us/insider/wiki/insider_wintp-insider_install/how-to-perform-a-repair-upgrade-using-the-windows/35160fbe-9352-4e70-9887-f40096ec3085](http://answers.microsoft.com/en-us/insider/wiki/insider_wintp-insider_install/how-to-perform-a-repair-upgrade-using-the-windows/35160fbe-9352-4e70-9887-f40096ec3085)

But it can be a bit tricky trying to make a  Windows bootable flash drive from Linux. Many Linux tools do not work. I think this does for Windows, I know it works for Linux:

 If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

---

### Post by khoriam on 2017-10-12
As from my experience, after you load live CD it offers installation, whereas in the left bottom corner a small button "fix computer" or something like that. Some time ago I had no problems with burning the windows disk image onto the flash drive with the help of startup disk creator.

---

