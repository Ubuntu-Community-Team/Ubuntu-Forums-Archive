---
title: "Can't Mount Windows 8 Partition"
date: 2013-06-16
forum: General Help
---

### Post by ashourism on 2013-06-16
Hi,

My windows 8 crashed, i installed Ubuntu 13.04 on another partition however, i can't access windows 8 files and i get this error whenever i try to mount

Error mounting system-managed device /dev/sda1: Command-line `mount "/mnt/94CCA009CC9FE430"' exited with non-zero exit status 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
 (udisks-error-quark, 0)

i followed this tutorial : [http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/) but i still can't access it and i get the same error

any suggestions?

Thanks

---

### Post by oldfred on 2013-06-18
If it needs chkdsk or is hibernated, the NTFS driver will not mount it normally to prevent further damage that chkdsk may not be able to fix.

If it crashed it may need chkdsk which you can only run from a Windows 8 repair console or repairCD or flash drive.

And if you resized Windows 8 using Linux it has to run chkdsk as it internally has to have partition size data that matches partition table.

But Windows 8 is always hibernated.
       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)


 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

Is install BIOS or from a pre-installed system with UEFI?


 [http://www.eightforums.com/](http://www.eightforums.com/)

---

### Post by tgross35 on 2013-06-18
It may also be worth running a checkdisk. Boot up Windows, open command prompt, and type "chkdsk -f -r c:". Reboot and let it run (note that this will take a long time, at least 3 hours to about 8 depending on your hard drive size.)

---

### Post by m1dnight on 2013-10-29
I had the same issue today.

I fixed it by completely disabling hibernation. Just having the option on creates an "hiberfil.sys" file on your C:\ drive the size of your ram. If you disable hibernation it gets deleted automatically.

To disable hibernation run a cmd as administrator and type:

powercfg -h off

if you reboot now you should be able to mount your Windows drive properly.

---

