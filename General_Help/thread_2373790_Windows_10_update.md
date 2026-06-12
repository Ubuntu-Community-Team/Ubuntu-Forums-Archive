---
title: "Windows 10 update"
date: 2017-10-09
forum: General Help
---

### Post by Tony_Palermo on 2017-10-09
I had to update Windows 10 to the current version now I don't have access to Ubuntu.  If I go into Ubuntu live can I some how re-install or re-scan grub so I can access both Windows and Ubuntu?

Thanks,

Tony

---

### Post by yetimon_64 on 2017-10-09
Here is a link to some community documentation for reinstalling access to ubuntu after a windows install (or in your case a Win10 update)...

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Regards, yeti.

---

### Post by oldfred on 2017-10-10
UEFI or BIOS?

If UEFI, you should just be able to reset UEFI boot order. 
You should be able to do that from within UEFI or with efibootmgr from inside Ubuntu.
And if UEFI you can boot Ubuntu from UEFI boot menu, even if Windows is now default.

But if BIOS, Windows (for years) has bug. When it updates it rewrites partition table and "forgets" to include any Linux logical partitions. Partition data is still there & you just need to fix partition table to re-add missing partition(s). You may have to reinstall grub.

       backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT_sda.txt
So you know sectors:
sudo parted /dev/sda unit s print 

I noticed new versions of testdisk now use sectors, so easier to use as existing partitions will show same sector info as parted. It used to use the very old CHS and was harder to use.

      
 [SOLVED] Windows 10 update, Stuck in grub rescue 
[URL="https://ubuntuforums.org/showthread.php?t=2373061"]https://ubuntuforums.org/showthread.php?t=2373061
[/URL]
 Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331) 
      
 Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462) 
    [URL="https://ubuntuforums.org/showthread.php?t=2373061"]
[/URL]

---

