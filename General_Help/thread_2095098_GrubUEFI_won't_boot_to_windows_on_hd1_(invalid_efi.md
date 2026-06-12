---
title: "Grub/UEFI won't boot to windows on hd1 (invalid efi file path)"
date: 2012-12-15
forum: General Help
---

### Post by samlev on 2012-12-15
So I have a new machine set up, and I'd not come across EFI before (it's been a few years since my last build).

After figuring out that I needed to set up an EFI partition before installing ubuntu, I've gotten to the point where I can actually boot now. Huzzah!

After installing ubuntu on hd0, I've gone and installed windows 7 on hd1. More fighting with grub and boot-repair later, and I have grub running in EFI mode with a Windows 7 option. Problem is that it doesn't work.

I've tried following advice from whatever sources I could find, and managed to destroy grub a few times, so I figure that it's probably about time to admit that I won't solve this myself.

So here is the paste from my last run of boot-repair:

[http://paste.ubuntu.com/1442915/](http://paste.ubuntu.com/1442915/)

You may also notice this entry in that log:
```

menuentry "Windows 7 - the correct one" {
set root=(hd0,1)
drivemap -s (hd0) (hd1)
chainloader +1
}

```

Which was my attempt at working around the issue following advice from the [Archlinux wiki](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems). It didn't work (unknown command drivemap).

Anyway, any help would be greatly appreciated.

**A summary of my drives:**
hd0,1 - EFI partition (/boot/efi)
hd0,2 - swap
hd0,3 - ubuntu 12.10 installation (/)

hd1,1 - Windows 7 installation

hd2,1 - NTFS storage drive (no OS, just files)

hd3,1 - /tmp for ubuntu
hd3,2 - /var for ubuntu
hd3,3 - /home for ubuntu

---

### Post by TOMBSTONEV2 on 2012-12-15
I believe you have just stumbled across a bug, a friend of mine had this same problem and he solved it with boot-repair. [http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by oldfred on 2012-12-16
I really prefer to have each system installed so if one drive fails, you can boot from the other. But your install of Windows in sdb found the efi partition in sda and used it. So you boot from sda to load Windows in sdb. With Windows & UEFI, you just about have to disconnect the other drive.

From UEFI menu does Windows boot correctly?  It normally wants a small unformulated partition for code MSR partition.

Even grub creates an incorrect chain load entry for Windows, but Boot-Repair creates the correct one.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)

    
       Wrong style chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
All these entries will not work.
'Windows ...) (on /dev/sdXY)'
Boot-Repair says it added correct entires but I do not see them in 25_custom??
> 
Add /boot/efi Microsoft efi entries in /etc/grub.d/25_custom Add /boot/efi Boot efi entries in /etc/grub.d/25_custom
       UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

---

### Post by samlev on 2012-12-16
Turns out that the problem was windows all along. It wouldn't install in EFI mode off the DVD, and I couldn't get a bootable USB stick to work in UEFI mode (if I formatted the stick with NTFS, it would work as a boot device, but not in UEFI mode. formatting as FAT32 would show up in UEFI mode, but not boot).

In the end, I've wiped my ubuntu and windows partitions, and started again, this time installing windows first (I was hesitant to do that at first because I was nervous about losing my OEM licence key if my hardware didn't work properly. I wanted to test with ubuntu to make sure it was all stable).

Everything is installed in Legacy/BIOS mode now, because I have no need for UEFI features (neither of my boot drives are over 2TB).

This has been... a long, long, experience. The thread can get marked as solved now, though.

---

