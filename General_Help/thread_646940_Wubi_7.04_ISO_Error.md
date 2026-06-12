---
title: "Wubi 7.04 ISO Error"
date: 2007-12-21
forum: General Help
---

### Post by deplanear on 2007-12-21
Below was previous post, but now after downloading ubuntu-7.10-alternate-i386.iso manually, I got the following error during install after reboot:

> 
Booting 'Ubuntu'

(hd0,0)

Filesystem type is fat, partition type 0xc
	[Linux-bzImage, setup=0x1c00, size=01a82cc]
	[Linux-initrd @ 0xf81e000, 0x7918a5 bytes]
Loading, please wait...
No RAID disks
	Check root = bootarg cat /proc/cmdline
	or missing modules, devices: cat /proc/modules ls /dev
ALERT! does not exist. Dropping to a shell!


BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)



-----
Hi all, been using Wubi for about 3 months and LOVE it, but I tried a new install on a different PC and I had this problem:

When I run Wubi (Wubi-7.04.04.exe as downloaded from the wubi site frontpage), and I select my various options (Ubuntu 6gb install), I get the following pop-up:

"Please download manually the disired (sic) ALTERNATE ISO into: c:\wubi\install"

I downloaded the latest alternate ISO (ubuntu-7.10-alternate-i386.iso) and put it in said folder, and also copied the iso to the folder where the wubi exe is, but receive same message during install.

I'm currently downloading the Ubuntu 7.04 alternate iso - which looking thru the docs and forum should work - but the reason I'm reporting is because A> I can't tell why I got this error in the first place, and B> the [WubiGuide]("https://wiki.ubuntu.com/WubiGuide") has the following confusing section:

> How can I use a manually downloaded ISO?

You need to download the appropriate ISO of the appropriate version. Place the ISO in the same folder where you have Wubi-7.04-XYZ.exe. Then run Wubi.

Note: 7.04 requires the ALTERNATE ISO 7.10 requires the DESKTOP ISO 

Perhaps it's the lack of punctuation, but this suggested to me that I download the 7.10 image; now that I look it over again it seems to imply that Wubi 7.10 requires the Desktop ISO. If someone can clarify this, I'll happily edit it myself in the wiki.

Thanks! (And, seriously, I've loved this utility SO much. Allows for super-easy install/uninstall as often as I'd like... which is often.)

---

### Post by ago on 2007-12-25
Is this win98?

---

