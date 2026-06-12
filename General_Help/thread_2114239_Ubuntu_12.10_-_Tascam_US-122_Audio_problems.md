---
title: "Ubuntu 12.10 - Tascam US-122 Audio problems"
date: 2013-02-09
forum: General Help
---

### Post by eboats on 2013-02-09
Hello, I'm trying to get my Tascam US-122  Audio interface working with Ubuntu 12.10 on my new Dell Inspiron 3520  (64 bit) laptop and am having problems.  I followed the steps at :

[https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122)

I can get the Tascam light to show Green but I can't get any sound out  of it (I have the Tascam audio outs going to my mixer and want to play  back music from my music software).  When I go to System Settings/Sound,  I do see the US-122 in the Output tab  (though have to unplug/re-plug in the usb cable in order for it to show  up).  So, I'd expect that because it shows up in the Output tab, that'd  I'd be able to get some sound, but no luck.  

When I do a   cat /proc/asound/cards   I see the card :

 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf7d00000 irq 44
 1 [USX2Y          ]: USB US-X2Y - TASCAM US-X2Y
                      TASCAM US-X2Y (1604:8007 if 0 at 001/013)

I was able to get this Tascam US-122 working with an older version of Ubuntu (11.10).  I don't have any problems with sound from my internal sound card.

  Any idea how to troubleshoot/fix the issue?

---

### Post by XeNtYhf on 2013-10-19
Hi, I got stuck on step 6 on this guide: [https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122)
When I type in sudo fxload -s /alsa-firmware-1.0.19/usx2y-fw-0.1b/ld2-ezusb.hex -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx -D /dev/bus/usb/001/022
I get the message: /alsa-firmware-1.0.19/usx2y-fw-0.1b/ld2-ezusb.hex: unable to open for input.
I cannot see what I am doing wrong. Can anyone help me? This is driving me mad!
Gerard

---

