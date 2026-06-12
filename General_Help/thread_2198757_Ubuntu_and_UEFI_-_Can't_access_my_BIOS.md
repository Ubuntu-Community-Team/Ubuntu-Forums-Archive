---
title: "Ubuntu and UEFI - Can't access my BIOS"
date: 2014-01-10
forum: General Help
---

### Post by xchawlez on 2014-01-10
I've recently installed Ubuntu 13.10 on my computer,  which was previously running windows 8. What I want to do is get rid of Ubuntu and install Windows 7 Professional 64 bit. I'm having a lot of troubles because I can't access my BIOS, none of the "F keys" have worked when booting. I can't boot from my live cd to install Windows 7.  

Computer Specs - Acer Aspire V5-551 p, 6gb RAM, Intel i5 @ 1.7ghz x 4 ... This was an originally Windows 8 machine.

Any help will be much appreciated !

I really need this fixed because I use this computer for school everyday, and I really need windows Instead of  Ubuntu!
Thanks :)

BTW, I've never posted on a forum before so I'm not quite sure how it works...

---

### Post by xchawlez on 2014-01-10
I recently replaced Windows 8 with Ubuntu 13.10, Ubuntu is now the only OS on my computer, I would like to remove it and Install windows 7, I have the install disk but I can't access the BIOS to make that boot. My computer BIOS (UEFI) can't be accessed by a function key or ESC, any help would be much appreciated!

I'm not sure if my System specs is needed but here they are,
Acer Aspire V5-551P (it's a laptop)

Intel i5-3317U 1.7ghz x4
Intel HD grapics 4000

---

### Post by Mark Phelps on 2014-01-10
Sorry I don't have good news -- but from what I could find doing a search,  the BIOS is set up from the factory so that you can only reach it from the Windows 8 environment.

Some folks have said that if you press F2 just at the right time, you can get to the BIOS but if it is set in UEFI mode, even that doesn't work.

So, how did you enter the BIOS to install Ubuntu in the first place?

---

### Post by lisati on 2014-01-10
Threads merged, so that the community's ability to help isn't diluted.

---

### Post by oldfred on 2014-01-10
Video on getting into UEFI - 1 Min Acer but all Windows 8
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI)

These are dual boot, but they may have posted more info.

 How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)
Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)
Added new msata drive post #3
[http://ubuntuforums.org/showthread.php?t=2174844](http://ubuntuforums.org/showthread.php?t=2174844)
Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)

You can install Windows 7 in UEFI mode if 64 bit and converted to flash drive. Standard DVD is BIOS only.

 Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

---

### Post by xchawlez on 2014-01-10
I set it up by entering my BIOS through advanced startup on Windows 8, going into my UEFI settings and disabled it which turned on legacy

EDIT: Guy's, I'm just gonna stick with Ubuntu, I installed Wine so It'll be fine for now. Thanks for the help :)

---

### Post by mlloyd on 2014-12-22
> **xchawlez said:**
> I've recently installed Ubuntu 13.10 on my computer,  which was previously running windows 8. What I want to do is get rid of Ubuntu and install Windows 7 Professional 64 bit. I'm having a lot of troubles because I can't access my BIOS, none of the "F keys" have worked when booting. I can't boot from my live cd to install Windows 7.  

Computer Specs - Acer Aspire V5-551 p, 6gb RAM, Intel i5 @ 1.7ghz x 4 ... This was an originally Windows 8 machine.

Any help will be much appreciated !

I really need this fixed because I use this computer for school everyday, and I really need windows Instead of  Ubuntu!
Thanks :)

BTW, I've never posted on a forum before so I'm not quite sure how it works...

UEFI is a replacement for BIOS. It is not BIOS. It supports both the new style (GPT, often cslled UEFI boot) and the old style (MBR, often incorrectly called BIOS boot but no BIOS is involved here) booting.

As for accessing the setup program:

I have used 4 systems with UEFI. All allowed pressing a key at startup. You might not be told about it but it should work. However, you may need to try multiple keys. I try DEL, F1, and F2.

There may be a setup option on the grub menu. That accesses the setup program.

If all else fails, startup with no boot device attached. That has worked for me on one system. Of course, that could be difficult on a laptop.

---

