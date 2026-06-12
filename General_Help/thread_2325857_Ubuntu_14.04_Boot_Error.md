---
title: "Ubuntu 14.04 Boot Error"
date: 2016-05-26
forum: General Help
---

### Post by HBZYU on 2016-05-26
Before I had any problem, I have Ubuntu 14.04 dual booting with multiple Windows 7.
I have 2 hardrives: 500GB(/dev/sda) and 2.0TB(/dev/sdb)
I have 2 Windows installed in 500GB drive. 2 Windows installed installed in 2.0TB and Ubuntu installed in 2.0TB drive.

Recently, I tried to install additional ArchLinux on my 2.0TB drive. I followed instructions and made 2 new partitions - one for /root and /home , another one for swap. And skipped the part that involves installing GRUB loader.
However, when I attempt to boot into ubuntu. 
I get a error message: ```
 [COLOR=#111111][FONT=Consolas]error: attempt to read or write outside of disk 'hd1'[/FONT][/COLOR]
```

After searching on the internet, I was able to get back to the grub menu by loading the Ubuntu liveCD and doing update-grub.
However, when ever i try to boot any os, I will get the "attempt to write outside" error or
```
[COLOR=#000000][FONT=Ubuntu Mono]kernel panic-not syncing: VFS: unable to mount root fs on [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]unknown block(0,0)[/FONT][/COLOR]
```

Eventually, I delete the 2 new ArchLinux partition I made, I thought it might be messing the Grub loader up. But I'm still unable to boot into Ubuntu.
Then I tried the Boot-Repair tools and ran the "Recommended Repair"
This is the result: [http://paste.ubuntu.com/16702385/](http://paste.ubuntu.com/16702385/)

Now I'm getting an message: ```
 [COLOR=#111111][FONT=Consolas]error: attempt to read or write outside of disk 'hd0'[/FONT][/COLOR]
```
Did the tool install another grub loader and made the matter worse?

Hope someone could shed some light how to proceed. Thanks!

---

### Post by T.J. on 2016-05-28
In order to help you, I need to know how old your computer is.  Some older chipsets do not support 2 TB drives properly.

---

### Post by oldfred on 2016-05-29
May be related to exfat, there is an exfat driver now, have you installed it?
Why exfat? may be required for some devices, but if dual booting best to stick with NTFS.

I would also keep the Windows boot loader on sda and only have grub on sdb.
With two MBR, no need to use EasyBCD and the ancient grub4dos to chain load.
And keep Ubuntu's grub in sdb, and set BIOS to default boot from it.
Do not use Boot-Repair's auto fix as that always installs grub to every MBR.

I do not see any specific partition issues. Sometime that error is from incorrect partition tables.

Note that Windows only boots from  the one primary NTFS partition with the boot flag on the drive BIOS has as default boot. It looks like sda1 for you.
Grub does not use boot flag to boot at all. I might put boot flag on one of your installs in sdb.

You can copy boot files or repair each Windows install by moving boot flag & repairing, so you can directly boot from grub if you want. 
Grub does not use boot flag, but looks for bootmgr & /Boot/BCD to know what partition Windows boots from.

---

