---
title: "Cannot boot after using Boot Repair in UbuntuGNOME"
date: 2017-07-14
forum: General Help
---

### Post by nitroaucity on 2017-07-14
I'm pretty new to Linux and wanted to try it on my Windows 10 machine, so I set up dual booting for the latest version of UbuntuGNOME by following this video: [https://www.youtube.com/watch?v=qNeJvujdB-0 ]("https://www.youtube.com/watch?v=qNeJvujdB-0")

I followed the video as closely as possible (except I chose "Install Ubuntu with Windows 10" instead of "Something Else), and the install succeeded but when I rebooted, it took me straight to Windows 10, and I didn't see the grub menu. I tried fixing this by installing Boot Repair using the Terminal and did the "Recommended Repair" and it said "Boot successfully repaired." once finished. I restarted once again.. and for a few seconds all I see is:
> [I]Failed to open \EFI\BOOT\grubx64.efi: Not Found
Failed to load image \EFI\BOOT\grubx64.efi: Not Found
start_image() returned Not Found.[/I]

After that, the screen went black and new text popped up saying:
> [I]Reboot and Select proper Boot Device
or Insert Boot Media in selected device and press a key[/I]

I have no idea what it did to my Windows boot files and grub files. Help would be appreciated.

EDIT: I generated a boot info file using Boot Repair in case if it's needed: [https://gist.github.com/anonymous/930d38878bcba7240666a7f876714e34](https://gist.github.com/anonymous/930d38878bcba7240666a7f876714e34)

---

### Post by oldfred on 2017-07-14
You have an UEFI system. But have installed a BIOS boot copy of grub to gpt drive's protective MBR.
That will never be used, so we leave it, but never try to boot in BIOS mode or it will just give grub errors.

You show all sorts of mount issues.
Most are probably caused by leaving Windows hibernated or its fast start up on.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Since UEFI system you should be able to directly boot Windows from UEFI boot menu, often f10 or f12, check your manual. And then be sure to turn off fast start up. Make a Windows repair disk.

 Grub only boots working Windows and Boot-Repair cannot do most Windows fixes. And Windows on updates will keep turning on fast start up. And any abnormal shutdown will require chkdsk which you can only do from Windows repair console.

Not sure why it is showing ext4 partition as having issues. Did you force shutdown or have power failure. And you must have had a working system to get grub installed (incorrectly) to MBR.

       
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 
    
 
       
 To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda4 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda4
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda4


 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

