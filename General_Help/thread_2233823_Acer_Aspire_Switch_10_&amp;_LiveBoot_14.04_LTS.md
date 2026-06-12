---
title: "Acer Aspire Switch 10 &amp; LiveBoot 14.04 LTS"
date: 2014-07-11
forum: General Help
---

### Post by Reggie_Guevara on 2014-07-11
[INDENT]Hi,
 
I'd like to liveboot ubuntu on my Switch 10 before installing it. The best reference I could find is [http://community.acer.com/t5/2012-Archives/UEFI-and-quot-Secure-Boot-quot-W510-and-maybe-W7xx/m-p/17707#M6215.](http://community.acer.com/t5/2012-Archives/UEFI-and-quot-Secure-Boot-quot-W510-and-maybe-W7xx/m-p/17707#M6215.)
 
But this was back in 2012. From my own experience, disabling SecureBoot doesn't do anything. I've tested my ubuntu usb & it works on my Acer Aspire 1825ptz. Directing my bios to boot from usb says system doesn't have usb boot capability.
 
I don't want to install Ubuntu yet until I've tested it on the hardware of my Switch 10.
 
Any advice?
 
Thanks.
 
Reggie


[/INDENT]

---

### Post by Bucky Ball on 2014-07-11
*Thread moved to **General Help**.*

Welcome. Burn a Live USB and boot from it. As you only want to try, you shouldn't need to switch off secure boot or anything else as you are running from the DVD/USB install, not the hard drive and you are not installed there.

This will not interfere with anything on your hard drive or system.

---

### Post by Reggie_Guevara on 2014-07-14
I've tried booting from LiveUSB both with SecureBoot enabled & disabled, but I go straight to Windows 8.

---

### Post by claire3 on 2014-07-14
Check this out: [http://ubuntuforums.org/showthread.php?t=2234219&p=13073540#post13073540](http://ubuntuforums.org/showthread.php?t=2234219&p=13073540#post13073540)

The issue is that the firmware on the Switch 10 can't boot a 64-bit UEFI bootloader. I also found a blog post from someone who used the 32-bit UEFI bootloader to install and boot 64-bit Ubuntu here: [http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/](http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/)

I'll keep my thread updated with progress...

---

