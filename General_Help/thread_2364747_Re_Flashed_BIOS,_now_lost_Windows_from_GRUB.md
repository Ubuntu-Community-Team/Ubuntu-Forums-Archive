---
title: "Re: Flashed BIOS, now lost Windows from GRUB"
date: 2017-06-27
forum: General Help
---

### Post by pablosquared on 2017-06-27
I stupidly decided to update the BIOS on my homebrew dual boot (Win 10 / Ubuntu 17.04) system, spec:

[B]ASUS Z170-P D3 m/b
8GB
1x 250GB SDD containing Windows and Ubuntu partitions
1x HDD data only drive, NTFS
UEFI mode (I think)[/B]

The BIOS update was a problematic process - I experienced a known looping issue with Internet BIOS updates - but it completed successfully first time. Once I resolved the BIOS boot loop, the system booted straight into Windows, no GRUB stage. I checked the HDD boot order, the Windows Boot Manager partition was 1st on the list, so I changed it to the SDD drive that contains GRUB. Now, it boots to GRUB but I've lost the option to select Windows, the only option is Ubuntu, which boots correctly when selected.

I presume the BIOS update has somehow reset the BIOS settings, but Fast Boot is disabled, as it was before. Secure Boot was enabled, where it wasn't before, but I've changed to disabled and I still don't see a Windows option at GRUB. I've tried grub-update, to no effect and I'm now at a bit of a loss as to how to restore Windows to GRUB.

Should I try boot repair (bit nervous using it with the UEFI boot - this is a fairly new system)? Or are there other BIOS settings to review first?

Lesson learned re: BIOS updates... Basically, don't!

TIA, PP

Forgot to say, Ubuntu can see the content of the Windows partition, and the EFI partition is present.

---

### Post by howefield on 2017-06-27
Thread moved to the "*General Help*" forum.

---

### Post by oldfred on 2017-06-27
Run Boot-Repair but only the report, do not do any fixes until someone reviews report.
       May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version not ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[URL="https://sourceforge.net/p/boot-repair/home/Home/"]https://sourceforge.net/p/boot-repair/home/Home
[/URL]
My old BIOS systems I had to take photos of all the settings I change. Every BIOS update reset everything back to defaults. 
With newer UEFI systems, they do save some settings, but mine offers both a list to what settings are changed when updating settings &  has a screen shot capability.
I find with BIOS or UEFI I have to change a lot of settings. And updates often can be required to have system work correctly.

My Asus is a slightly older version, but may have very similar UEFI.

 Asus-ar screenshots oldfred
[http://ubuntuforums.org/showthread.php?t=2258575&page=2](http://ubuntuforums.org/showthread.php?t=2258575&page=2)

---

### Post by pablosquared on 2017-06-27
Thanks so much, oldfred. Very helpful. I'll go get stuck in now and report back ASAP.

---

### Post by pablosquared on 2017-06-27
Boot-Info report below. I'll check your BIOS settings against mine and try booting again.

[URL="https://paste2.org/ajtkaKB0"]https://paste2.org/ajtkaKB0

[/URL]

---

### Post by oldfred on 2017-06-27
You show Windows installed in UEFI boot mode on gpt partitioned drive.

Because fstab has a mount of the ESP - efi system partition your Ubuntu install is UEFI bootabe.
But you have an old grub installed in BIOS boot mode in gpt's protective MBR. Not otherwise used, and often more dangerous to erase than just leaving grub in MBR, but never try to boot in BIOS/CSM/Legacy boot mode. Always use UEFI.

You also have boot flag on two partition. Almost all systems only allow only one per device/drive. Remove boot flag from sda4.

Boot flag is used by Windows in BIOS mode to indicated which NTFS partition has boot flags. But in UEFI boot mode, boot flag with gparted assigns the correct GUID internally (ESP) for UEFI to know which partition has all UEFI boot files for all systems. Other programs use different codes like gdisk uses ef00 to assign the ESP partition/GUID.

It looks like you booted Live Installer in BIOS/CSM mode. Always boot repair media in UEFI mode also, since installed systems are UEFI.

---

### Post by pablosquared on 2017-06-27
Thanks again. I confess that when I installed Linux, I wasn't really sure what I was doing and it took a bit of trial and error before I got GRUB working with the Windows 10 install. From what you've said, I didn't do it optimally, let's say. 

I wonder if it would be better now to reinstall Ubuntu in UEFI mode - nothing I do in BIOS is bringing Windows back to GRUB. If I change CSM in BIOS to UEFI only, Windows boots immediately, no GRUB stage. (And I just got the Creator's update, which took ages to download and install, including 3 reboots, dammit...). What do you think?

---

### Post by oldfred on 2017-06-27
You should not have to reinstall.

Both Windows & Ubuntu reset UEFI to make it first in boot order on major updates.
So you often have to reset UEFI boot order.

You should be able to go into UEFI and make grub/Ubuntu entry first and Windows 2nd in boot order.
And you should always be able to directly boot either Ubuntu or Windows from UEFI boot menu often f10 or f12. But if you have fast boot on in UEFI, you may not be quick enough to press any keys. I reset my system to allow 3 sec delay in warm/reboot and normal boot from full power down. So then I have just enough time on a warm/reboot or if necessary can fully shutdown and do a full cold boot.

You can also in Ubuntu use efibootmgr to reset boot order.
To see order:
sudo efibootmgr -v
see also for more details:
man efibootmgr

Windows on updates will also turn its fast start up back on. You need that off normally to boot Windows from grub menu. Although someone just posted that it still worked with fast start up on. I know they were updating grub, but did not know that was one of fixes. 
But with fast start up on, all the NTFS partitions are in  a hibernated state and you cannot read/write from Ubuntu.

 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions](http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions)

---

### Post by pablosquared on 2017-06-27
Ok, so I've tried to look at EFI setting on Linux.

```

pablo@Ubuntu:~$ sudo efibootmgr -v
EFI variables are not supported on this system.
pablo@Ubuntu:~$ 


```

Not sure if that's because of how I installed Linux originally. Is there another way to review / change the UEFI boot order, other than in BIOS which I've done earlier and didn't fix the problem? Also, do you have any idea why updating the BIOS removed the Windows boot option from GRUB without an update-grub process in Linux?

Interesting to read about Windows updates switching fast boot back on. I've had experience of that where, after a Windows Update (not every time), Linux is unable to read the NTFS-formatted data drive. I stumbled upon the fix, which was to boot into Windows again, then boot back into Linux, whereupon the NTFS data drive was readable again. Very annoying, but easily fixed.

---

### Post by oldfred on 2017-06-27
If you cannot read UEFI variables, you probably have booted in BIOS boot mode.

It looked like your system was installed in UEFI boot mode, but it may be possible to boot in BIOS mode if correctly configured. Some have had systems set up to boot either way UEFI or BIOS boot mode, but often updates in one mode eventually prevent booting in other mode.

---

### Post by pablosquared on 2017-07-04
Quick update to confirm that this issue is resolved. I installed rEFInd ([http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)) which resolved the issue and installed a new boot manager that allows me to select Ubuntu or Windows. Thanks to oldfred and Roderick Smith, rEFInd developer for their help.

---

