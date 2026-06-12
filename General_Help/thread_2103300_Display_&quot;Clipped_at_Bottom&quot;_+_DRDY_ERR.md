---
title: "Display &quot;Clipped at Bottom&quot; + DRDY ERR"
date: 2013-01-09
forum: General Help
---

### Post by silbernetic on 2013-01-09
Good Evening-

tl;dr version: about 200 pixels will not show up at the bottom of my screen. it is not just in Ubuntu but Windows and even the BIOS screen, before any boot environment is loaded. I also was having some issues with what may be bad blocks.


So, I am the owner of an ASUS Eee PC 1015PE (netbook). I got it a few years back, and this thing has been through a lot. It's in reasonably good physical condition as well as software. I did step on the screen about a year back so I had to replace that, and it broke a snap, leaving the plastic shell a bit apt to open up. On the side, it runs Ubuntu Lucid Lynx, I think "netbook edition." It used to run UNR before that ended.

It was earlier today that without any real changes, I noticed the bottom of my screen was getting cut off. It is still active, the cursor seems to register as existing there, and xrandr reports 1024x768 mode. Now that in and of its self is interesting - the 1015PE's screen can only really support 1024x600. Any time I wanted 1024x768 it would require special scrolling. The really, really interesting part, though, is that this is not confined to the OS. Or any single OS. Or even 1024x768, but also 800x600. I can boot up and the BIOS prompt is clipped, Windows 7 in the dual boot is clipped, tty1 is clipped... And it all looks like it's 168 pixels that are gone.

To compound things, it started giving a DRDY ERR message, or something along those lines when I tried to boot again. This was probably just a nasty power-down, I'm going to try and squeeze BackTrack on a flash drive to force an fsck. That isn't a huge concern, it just means I can't boot to Ubuntu (Lucid) until then.


So, I also did some investigation with xrandr, and it will not recognize 1024x600 as a supported mode. I worried it was a hardware issue, so I checked the cables between the screen and the mobo and they seem to be all okay. I also looked at flashing the BIOS as it is a couple of years out of date, but I ran into some issues on the side and put that on the back burner.

Is there anything I'm missing in fixing this issue with my display? I believe my replacement I fitted may have been aftermarket, but I don't think it would fail after so few hours of usage. Let me know what you guys think.

Best,
silbernetic

---

### Post by silbernetic on 2013-01-10
Updates:

I have flashed the BIOS to the most recent version. No change in results.

I fixed the disk with fsck after booting into another Ubuntu copy off of an SD card. Boots and functions now, but the same issue with the display is still happening.

---

