---
title: "Need GRUB menu entry for Microsoft Vista"
date: 2007-06-21
forum: General Help
---

### Post by brn on 2007-06-21
Grappling with a wireless problem on a Compaq C500 laptop that came with Vista pre-installed, I decided to try reinstalling Dapper (I had Fiesty).  Somehow the GRUB menu has lost all reference to Vista, although it is still on the drive and everything else works fine.  The manual for GRUB v0.97 doesn't show any specific examples for Windows boot sequences so I'm at a loss as to just what to edit into the menu.  A menu entry for Linux looks like this:
> title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot
Would someone with Ubuntu/Vista dual boot working kindly post the relevant Vista passages from /boot/grub/menu.lst here to guide me?

Thanks

PS:  I really don't miss Vista but until I can make the wireless card work with Ubuntu my new laptop is just an over-priced desktop machine.  -Please help-

---

### Post by johnnyoc3 on 2007-06-21
i have a working dual boot with vista. hold on and let me boot to ubuntu and post a copy. however you may need to change the number after the hard drive to correspond to the vista partition

---

### Post by empthollow on 2007-06-21
i don't have vista but his is the typical entry for booting anything that isn't linux
```
title        not linux
root        (hdx,x)
chainloader    +1
```

the x,x would be replaced with you hard drive and partiton.
if you do an ```
fdisk -l
```

---

### Post by johnnyoc3 on 2007-06-21
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista
root		(hd0,2)
savedefault	1
makeactive
chainloader	+1
```

---

### Post by brn on 2007-06-22
...Thanks both...  I tried the exact format shown by johnnyoc3 but this produced a GRUB error   ("FS type ext2")  so I changed (hd0,2) to (hd0,1) which brought up Vista in recovery mode.  Following the instructions I reloaded the entire thing (2.5 hours!) and got it to work.  Then I *_carefully_* re-installed Dapper.  Now I'm back where I was yesterday, with no Vista.

The only thing I saw that seemed remiss yesterday was that fdisk showed the boot flag set at /dev/sda3, the linux / partition.  Now it appears at sda1 the Windows partition, but the GRUB menu is still missing the needed entry for Vista.  What to try next?

I wonder how the partition numbering system works.  If it starts at zero the incantation to boot from Windows would probably be (hd0.0).  This would be consistent with what I saw this morning since what I assume is the Windows "recovery disk" is in the second partition (sda2 according to fdisk).  I suppose I'll try this next but any and all advice is warmly appreciated.

Thanks again

[COLOR="DarkRed"]...That worked!..  Pointing the loader to hd0.0 brought back Vista in all its "glory".  --WHEW!--[/COLOR]

---

### Post by logos34 on 2007-06-22
I really wish I had saved my RC1 prereleases of Vista I downloaded last year as part of that Microsoft promo, then at least I could test out why some are having problems dual-booting vista and linux, while others seem to to have none at all.  But I will never purchase Vista and so I guess I'll never know exactly how Grub and Vista get along (or don't).  

This is from the top of the [WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot") howto:

> 
Windows Vista notes

Windows Vista can shrink its own partition without the need to use third-party software. See [WWW] this link. If you are running Windows Vista, shrink down your partition through that method, and then boot Ubuntu. The Ubuntu installer will use the free space you created. **Windows Vista may stop your GRUB - Boot manager from reaching (booting ) your Ubuntu installation, when for any reason you try to repair Boot on MBR (Master Boot Record) on your Bootable HDD (Hard Disk Drive). To avoid such a mess many of you may opt to gracefully let Vista have the MBR, and its boot manager should then point to boot partition of your Ubuntu. Windows Vista no more boots through boot.ini and ntdetect.com and ntldr.** Instead a Boot folder stores all data for its new Boot Manager to load, Windows Vista OS ships with an command line utility called bcdedit.exe, used with administrator credentials of course. You may want to read [WWW] here about it. Using a command line utility has always its learning curve, so faster and better job can be done with a free utility called [WWW] **EasyBCD**, developed and mastered in times of VistaBeta already.

---

