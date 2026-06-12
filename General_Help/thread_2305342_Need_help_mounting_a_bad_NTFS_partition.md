---
title: "Need help mounting a bad NTFS partition"
date: 2015-12-04
forum: General Help
---

### Post by Evil Wayz on 2015-12-04
My Windoze comp crapped the bed, been using a live stick to use the computer.  I don't own a Winodws machine besides this one, so I can't mount the drive in windows and chkdsk it and reboot it twice like it keep insisting on.  so I though I'd get whatever data I could off it and buy a new hard drive.  Can't get the command right though.  I read the wiki and it keeps spitting options out at me.  

So what I need is the command to mount /dev/sdb4 to /media/windows (because it's simpler than that long string of letters and numbers and if it doesn't work I can always cut and paste it back in) 

Here's the output when I attempt to let Ubuntu try to mount the drive itself:  

[HTML]Error mounting /dev/sdb4 at /media/ubuntu/72F0ACC1F0AC8CC3: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999,dmask=0077,fmask=0177" "/dev/sdb4" "/media/ubuntu/72F0ACC1F0AC8CC3"' exited with non-zero exit status 14: Windows is hibernated, refused to mount.
Failed to mount '/dev/sdb4': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.[/HTML]

---

### Post by oldfred on 2015-12-05
Did you leave it hibernated or does it need chkdsk?

 Force removal of hiberfil from Ubuntu
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)
Force mount, read only:
sudo mkdir /media/windows
sudo mount -t ntfs-3g -o ro /dev/sda3 /media/windows

You always should have the Windows current installed version repair CD or flash drive and Ubuntu live installer current version installed. 

      
 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

    
A few third party Windows repair tools may do chkdsk. The Linux ntfsfix only turns on the chkdsk flag. But if you can start to boot you should be able to press f8 and get into repair console.

      
 Partition Wizard -  boot CD or flash also, chkdsk & other Windows repairs
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
[http://www.partitionwizard.com/partitionmanager/partition-fix.html](http://www.partitionwizard.com/partitionmanager/partition-fix.html)

   Third party chkdsk tools
Hiren's Boot CD, and do a chkdsk on the XP
[http://www.hirensbootcd.org/](http://www.hirensbootcd.org/)

---

