---
title: "what's the best way to troubleshoot this crash (I think?) issue?"
date: 2016-09-17
forum: General Help
---

### Post by jeebustrain on 2016-09-17
so I recently upgraded the cpu/mobo/proc of my (up until now) rock solid Ubuntu 16.04 machine. I kept the same ram, disks, and video card (Geforce 650). Old CPU was an Athlon XP, new one is an FX-8370. Now it's way faster, but it randomly (several times a day) seems to crash... basically going to a black screen and then rebooting after about 3-4 minutes. A continuous ping on the system shows it drop off the network immediately after the screen goes black.

This is what last tells me:
[http://www.viralmatrix.net/other/crash%200917.png](http://www.viralmatrix.net/other/crash%200917.png)

I can't seem to pinpoint the exact cause in the logs though. I first thought it may have been the video drivers, but I switched from both the proprietary Nvidia drivers to the open source drivers and it does it regardless. Temperatures seem to be ok (my old system used to regularly hover in the 56c range, this new one never goes above 35c or so. The video card temp is pretty nominal as well. I'm looking in syslog and there doesn't appear to be anything in there other than a regular reboot. 

I have noticed though that it tends to do it a lot more when I'm browsing the internet or doing anything that may be considered graphically intensive (it did it when I tried playing a game). It also seems to consistently do it when I'm looking at the f'n logging utility (which is infuriating!). I can let it sit and it seems to be a lot more stable, although it still does it.

Does anyone have any ideas on what I could look at next? I'm willing to accept that it may be a hardware problem, but I can't find ANYTHING that would indicate exactly what it could be.

---

### Post by jeebustrain on 2016-09-17
note - I've always done mobo/cpu swaps inside linux over the years (been using it off and on since SuSE 5.2, full time since about 2006) and have had zero problems up until now.

---

### Post by HereInOz on 2016-09-17
If you can, grab another hard disk and do a simple install using the new hardware and the new hard disk.  If you still get the issue, then it is a hardware issue (motherboard intermittently shorting to earth, or similar) or if the problem goes away, then you will need to concentrate on the installation.

I, too, have changed Ubuntu hard disks over to new hardware, and have even gone from and AMD processor to and Intel processor without any issues.  All the necessary drivers are loaded at boot up, so the system can cope with massive hardware changes, unlike another operating system which we all know and love :-(

I had a similar issue a few years back, and it was a USB port going to earth every few hours.

I would suspect you may have a hardware issue.

---

### Post by ian-weisser on 2016-09-17
Any clues in syslog or dmesg?

---

### Post by jeebustrain on 2016-09-18
ok thanks... did a bit more digging and saw that there was a BIOS upgrade (after reading about some stability issues people were having with that particular Mobo - Asus Sabertooth 990FX R2) - I was in the BIOS utility and it actually bounced right in the middle of trying to flash the BIOS. Obviously it didn't like that, so I tried to boot back in to flash it back to default, but it kept rebooting. Now it's pretty much bricked. 

I'm sending it back to Amazon - I'm pretty sure this mobo was toast when I bought it. I have a different model coming in on Monday.

Thanks everybody.


And Ian - no, there was no indication of any issues in syslog or dmesg (like literally nothing). From everything I could tell, Ubuntu saw it as a clean boot.

---

### Post by jeebustrain on 2016-09-22
In case anyone is interested, I got my new motherboard (this time changed chipsets from a 990FX to a 990X), and it's been rock solid (so far) for more than 24 hours. I'd read of people having issues with 990FX boards in Linux, and I wasn't doing any sort of extreme computing, so I figured the step down would be just find. So far it is!

---

