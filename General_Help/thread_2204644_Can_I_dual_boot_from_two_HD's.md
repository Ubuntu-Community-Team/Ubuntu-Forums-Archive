---
title: "Can I dual boot from two HD's"
date: 2014-02-09
forum: General Help
---

### Post by Easy Limits on 2014-02-09
I am thinking of putting Ubuntu on my new 128 Gb SSD and put Win7 on my 500Gb sata hard drive.  Will grub work for this or will I have to select which drive I want to access via the BIOS during boot-up?

---

### Post by oldfred on 2014-02-09
As long as both systems are UEFI or both BIOS, you can boot from grub menu.

I suggest also having a Windows boot loader on the Windows drive, so you can boot from BIOS if major issues, but normally boot from grub.

Best to uninstall SSD. Windows will put its 100MB boot partition on the drive you have set in BIOS to boot from. So if booting from SSD, it just will overwrite the first 100MB as it does not see Linux partitions.
If you change BIOS to boot hard drive before installing Windows it should work, but backups are important.

---

### Post by Easy Limits on 2014-02-09
Well, I tried to install Win7 on the 500Gb SATA drive after I installed Ubuntu 12.04 on the SSD and Windows would not let me install on the blank NTFS formatted SATA drive.

Do I need to switch the order of the installation process?  Meaning install Win7 on the SATA drive before installing Ubuntu 12.04 on the SSD?

I tried installing WIn7 and Ubuntu 12.04 on the SSD drive and I kept getting a Fatal Error in Ubuntu at the end of the install process, some sort of problem with GRUB.

---

### Post by Bucky Ball on 2014-02-09
> **Easy Limits said:**
> I tried installing WIn7 and Ubuntu 12.04 on the SSD drive and I kept getting a Fatal Error in Ubuntu at the end of the install process, some sort of problem with GRUB.

If you're installing in BIOS you may already have four partitions on the SSD. That is the limit. EFI doesn't have that limit. Not sure how many partitions Win7 spits out when it installs, but could be your problem.

---

### Post by Easy Limits on 2014-02-09
How do I know if I am installing in BIOS or EFI?  When I boot I see an ASUS Republic of Gamers UEFI screen.  Is that my clue?

---

### Post by oldfred on 2014-02-10
Do not know from Windows. But Windows 7 DVD default is BIOS and will not install to gpt drives, you have to convert to flash drive install and modify it slightly.

From Ubuntu you can easy tell if you get grub menu as that is UEFI, or purple accessiblity screen as that is BIOS.
       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

      
 Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[URL="http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx"]http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx

[/URL] Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

[URL="http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx"]
[/URL]

---

### Post by Easy Limits on 2014-02-14
Well, I got it to work.  I have Win7 on my 500Gb sata drive and Ubuntu 12.04 on my new SSD and a grub screen at boot up to select either.  The only weird thing is the grub screen shows the Debian splash screen not the purple grub screen.

---

### Post by Bucky Ball on 2014-02-14
> **Easy Limits said:**
> The only weird thing is the grub screen shows the Debian splash screen not the purple grub screen.

Normal. So does mine. ;)

You can change it if you want. Try Ubuntu Tweak, I think that does it, or Grub Customizer.

---

