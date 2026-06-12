---
title: "geforce 8400 gs - can it run 3 monitors at once - only getting 2 of 3"
date: 2012-12-01
forum: General Help
---

### Post by rocket777 on 2012-12-01
I have a geforce 8200 GS / 1gb display controller card. It has 3 outputs from left to right

DVI - HDMI - VGA

The bios comes up on the first that is plugged in. I've tried to hook up 3 at once but only 2 work at one time. 

With all 3 plugged into monitors, only the DVI and VGA show up. If I unplug the DVI, then the HDMI and VGA are seen in ubuntu.

Is this a limitation of the card, or is it something I need to do in Ubuntu?

---

### Post by dannyboy79 on 2012-12-03
yes, the card can only power 2 displays. which version of ubuntu? which driver are you using? I have an 8400 gs coming in the mail from newegg. I am running 10.04.4, I am hoping to power a 23" Olevia TV via VGA or HDMI but I am not sure which drivers ill need. Either nouveau or nvidia website binaries and if so, which version?

---

### Post by haqking on 2012-12-03
> **rocket777 said:**
> I have a geforce 8200 GS / 1gb display controller card. It has 3 outputs from left to right

DVI - HDMI - VGA

The bios comes up on the first that is plugged in. I've tried to hook up 3 at once but only 2 work at one time. 

With all 3 plugged into monitors, only the DVI and VGA show up. If I unplug the DVI, then the HDMI and VGA are seen in ubuntu.

Is this a limitation of the card, or is it something I need to do in Ubuntu?

Yes, that card wont support 3 monitors

---

### Post by rocket777 on 2012-12-03
> **dannyboy79 said:**
> yes, the card can only power 2 displays. which version of ubuntu? which driver are you using? I have an 8400 gs coming in the mail from newegg. I am running 10.04.4, I am hoping to power a 23" Olevia TV via VGA or HDMI but I am not sure which drivers ill need. Either nouveau or nvidia website binaries and if so, which version?

I have a tripple boot system, ubuntu 10.04, 12.04, and kubuntu 12.10.  I just kept adding systems hoping to solve my video issues. At first I had multiple cards, but couldn't find any way to get more than one to work at a time. On one of the 12's I ran the option to add drivers - but I suspect these drivers were to be for better 3d support. I saw no improvement using them for video.

I only use the 8400gs to power HD videos, and it seems to work best with the hdmi port. The mouse is jerky on the second screen over the vga port. But it does let me watch hd video at 1920x1080 32 bit using vlc player. 

Originally, I had intended this card to go in my windows quad core 2.6 system, but after not having a single freezed system in years, it froze 3 times in 2 days using this card. I suspect it could be that my power supply was reading 11.9 volts. In my dual core 2.8 system where I run the ubuntus, that PS reads 12.4 volts and so far no crashing.

Then again, I only paid $25 for the card, so I wasn't really expecting much.

---

### Post by dannyboy79 on 2012-12-03
in your ubuntu 10.04 system, do you use the 8400 GS? if so, which nvidia driver? Nouveau, Nv, Repo provided drivers (nvidia-current) or binaries from the Nvidia Website?

---

### Post by rocket777 on 2012-12-03
> **dannyboy79 said:**
> in your ubuntu 10.04 system, do you use the 8400 GS? if so, which nvidia driver? Nouveau, Nv, Repo provided drivers (nvidia-current) or binaries from the Nvidia Website?

Yes, I am leaving the 8400 gs in my ubuntu system(s). However, I didn't try any extra drivers in the 10.04 system, just one of the 12's. It's working ok over the hdmi port and now that I know I can't add a 3rd monitor, I'll just stay the way I am.

I'm pretty sure it was nvidia drivers that it added, I just remember it said they were proprietary.

---

