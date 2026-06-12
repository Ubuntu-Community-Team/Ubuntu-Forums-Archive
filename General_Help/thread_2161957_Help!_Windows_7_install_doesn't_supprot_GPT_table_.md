---
title: "Help! Windows 7 install doesn't supprot GPT table - but I want to keep Ubuntu!"
date: 2013-07-12
forum: General Help
---

### Post by zesterer on 2013-07-12
Hi there,

Recently I have required Windows for work (yes, I've tried WINE and virtualbox but they just don't cut it). I tried installing Windows 7 from a USB stick, but it said it could not be installed on the NTFS partition I set up because the driver had a GPT partition table.

This is a problem.I need Windows up and running quite urgently (tomorrow), but I already have Ubuntu install plus a few other partitions on the hardrive, and I DO NOT want to get rid of them!!!!

I need to set the partition table type to msdos WITHOUT erasing data. Either that, or I find a way to force Windows into installing on GPT. Which probably is impossible seeing as it's closed-source software.

Any ideas?  Thanks for reading!

Barry Smith (Z)

---

### Post by oldfred on 2013-07-12
Is your system new enough to boot with UEFI. Windows only installs on gpt partitioned drive with UEFI. Ubuntu will boot from gpt partitioned drives with either UEFI or BIOS, so are you booting with BIOS mode?
How you boot install media is how it installs. If Windows 7 and system is UEFI capable, I think you have to convert DVD to flash drive and make a few changes/updates to convert to install in UEFI mode.

There are ways to convert back to MBR. You would have to reinstall grub2 and have to have really good backups as any major system change has risks.

Is this a system where you can install another drive? I dual booted XP in BIOS/MBR and Ubuntu in BIOS/gpt for years. Or just install another hard drive to install Windows into? Good excuse to get a new SSD?

       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[URL="http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr"]http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr

[/URL] Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
Convert Windows USB flash install to UEFI boot
[http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/](http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

[URL="http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr"]
[/URL]

---

### Post by zesterer on 2013-07-12
My BIOS has a UEFI option, yes. Do I need to create a specific Windows 7 UEFI boot USB disk? If so, how can I do that from Linux?

I don't have another hardrive and can't get one :(. I've been looking around the internet a lot about this, and I think that I might need a special UEFI Windows 7 boot disk. Is this true?

Thanks for answering,

Barry

EDIT: Actually, I just saw the links you put at the bottom of your post. I didn't see them, I must have looked past them. I swear my brain has a built-in advert ignoring system ;) Thanks so much, I'll tell you if it works! :D

---

### Post by oldfred on 2013-07-12
The other question is, Is Ubuntu in UEFI mode or BIOS mode. If Ubuntu is BIOS mode with a bios_grub partition, you will need an efi partition which should be near beginning of drive. Then Boot-Repair can convert from BIOS boot to a UEFI boot by uninstalling grub-pc and installing grub-efi. You can also do that manually.

Windows requires several partitions. I think when it installs it will create them. Not sure what it does to efi partition, so if you have that with grub I would back that up first just in case.

If Windows 7, you will not have any of the secure boot issues and it should work without major issues. You will need unallocated space for Windows to install but with gpt there is no limit (well 128) on number of partitions.

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

