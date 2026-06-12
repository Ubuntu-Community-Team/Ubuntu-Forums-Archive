---
title: "Error Mounting Partitions (NTFS)"
date: 2014-10-06
forum: General Help
---

### Post by adnansanni on 2014-10-06
Hello guys,
I've been facing a problem on mounting my secondary hard-disk's partitions on Ubuntu 14.04.1 x64. Previously I had windows 8.1. I've Installed Ubuntu cleanly on SSD and everything is working fine. Now I've add my secondary HDD on PC but it has failed to mount. I've three partitions on that HDD and getting the same error:

----
Unable to access "Store"
Error mounting /dev/sdb1 at /media/adnan/Store: Command-line 'mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,dmask=0077,fmask=0177""/dev/sdb1""/media/adnan/Store"" exited with non-zero exit status 14: The disk contains an unclean file system (0, ,0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sdb1': Operation not permitted
The NTFS partitions is an unsafe state. Please resume and shutdown Windows fully (no hibernation or fast restarting), or mount the volume read-only with the "ro" mount option.
----

I'm sure that I've shutdown the windows before install the Ubuntu. and unplug this HDD and install Ubuntu on SSD. As it suggest resume the Windows and shutdown properly but the problem is I haven't the windows anymore. Any solutions other than install the windows again?

---

### Post by Habitual on 2014-10-06
Do you have fast boot enabled?
See also [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295) and/or [http://askubuntu.com/questions/439634/unable-to-mount-ntfs-hard-drive-partition-the-disk-contains-an-unclean-file-sys](http://askubuntu.com/questions/439634/unable-to-mount-ntfs-hard-drive-partition-the-disk-contains-an-unclean-file-sys)

---

### Post by oldfred on 2014-10-06
Did you make a Windows repairCD or flash drive. If you keep a NTFS partition you have to run chkdsk periodically and you can only do that from Windows. Ubuntu runs fsck on its partitions every 40 or 60 reboots, but you would not get any chkdsks on NTFS from Linux.

If it is just a hiberfile from the always on hibernation, you may be able to delete that. But probably still need chkdsk. Some third party Windows repair/partition tools may run chkdsk, but best to have Windows own repair tool. 

       [http://technet.microsoft.com/en-us/library/cc730714.aspx](http://technet.microsoft.com/en-us/library/cc730714.aspx)
    
 Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)
[http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx](http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx)

 Partition Wizard -  boot CD or flash also, chkdsk & other Windows repairs
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
[http://www.partitionwizard.com/partitionmanager/partition-fix.html](http://www.partitionwizard.com/partitionmanager/partition-fix.html)

If you have access to another Windows 8 system you can make your own repair. 
Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

We used to recommend a site that would let you download the free Windows repair CD for free, but now they charge $20 or $30.
        [http://neosmart.net/blog/2013/download-efi-and-uefi-repair-cds-for-windows/](http://neosmart.net/blog/2013/download-efi-and-uefi-repair-cds-for-windows/)

---

### Post by Mark Phelps on 2014-10-06
> Previously I had windows 8.1. Oh, oh!

If the external drive was connected when you were using Windows 8.1, when you "shutdown" 8.1, it actually went into hibernation -- and that included the external drive!

You can disable that in Win8. by disabling FastStartup. But, if you no longer have Win8.1, your problem now is that the partition on the External drive is "hibernated" -- and will remain that way until that is disabled.

If you don't have access to Windows anymore, you might be able to fix the problem using the Minitool Partition Wizard Boot CD link that oldfred provided.  Download the ISO, burn a CD from that, boot from the CD -- and see if the Check function will work on the External drive.

---

### Post by adnansanni on 2014-10-06
Thanks Habitual, oldfred and Mark Phelps for your replies.
Windows 8.1's fast start-up feature is really a stupid feature, it shouldn't be set by default. Because of it, windows can't load usb3 driver, can't detect new HDD until restart and now this problem. I've created image-backup for the windows for this PC but didn't make recovery disk. I've another laptop which has windows 8.1, I guess I can create a recovery disk from laptop and use it on the PC.
I think it should be safe to go back (reinstall) to windows and stop the fast start-up feature restart couple of times and then boot the Ubuntu with live disk, if I can mount the partitions then again reinstall the Ubuntu.

---

### Post by oldfred on 2014-10-06
While this is mostly discussing the now discontinued wubi, it mentions that EasyBCD can remove fast start & hybrid sleep from Windows. Not sure then if it works on just the data partition or not. It may just be a chkdsk that is required to reset it. And you can run the chkdsk from your Windows repair flash drive.

[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)

---

