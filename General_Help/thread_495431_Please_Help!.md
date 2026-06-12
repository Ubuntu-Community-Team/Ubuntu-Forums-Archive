---
title: "Please Help!"
date: 2007-07-08
forum: General Help
---

### Post by bomb-24 on 2007-07-08
I have a Hp Media Center 864n. I just installed Ubuntu 7.04 to replace my Windows XP OS. Everything is great. Except, My speakers wont work. and my remote control that controls my computer wont work either. Can anyone help me figure out how to fix this problem? I dont know what to do considering that im very new to Linux. Your help is greatly appreciated.

---

### Post by eggdeng on 2007-07-08
Start by identifying your sound card. Post the output from ```
lspci | grep Audio
``` If you get no output, try ```
lspci
``` on it's own. Post the output of ```
aplay -l
```

---

### Post by bomb-24 on 2007-07-08
This is what i got for those codes:


pickard83@pickard83-desktop:~$ sudo -i
Password:
root@pickard83-desktop:~# lspci | grep Audio
root@pickard83-desktop:~# lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)
02:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
02:09.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
02:0a.0 Multimedia controller: C-Cube Microsystems E4? (rev b1)
02:0b.0 Communication controller: Agere Systems LT WinModem (rev 02)
02:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0d.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01)
root@pickard83-desktop:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy [Audigy 1 [Unknown]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy [Audigy 1 [Unknown]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy [Audigy 1 [Unknown]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@pickard83-desktop:~# 

I am pretty new at this. This is 90 percent Jiberish to me. What do you think?

---

### Post by bomb-24 on 2007-07-08
Well, I think I just figured it out. I think. In the volume control settings, the Audigy Analog/Digital Output Jack, was check marked. I unchecked it and played one of my cds and its playing. Hopefully this took care of it. Now I have a problem with my remote control that controls my computer for like media or dvds or whatever you want to use it for isnt working. It can control alot of stuff, and I use it alot. Hopefully I can get some help on what I can try to do to get it to work. Id try anything. I would appreciate any help anyone has to offer.

---

### Post by Caxixi on 2007-07-09
Just wanted to say thank you to bomb-24 for posting his simple little fix with the Audigy Analog/Digital Output Jack checkbox. That just solved my sound issue! Yay for forum search!

Only 1 hour into my first install of Ubuntu, and here I am on the forums looking for and getting answers. This is exciting!

Caxixi

---

### Post by strabes on 2007-07-09
bomb-24: Could you be more specific in your question about the remote? What model is it? Have you searched the forums for it? Have you looked through the community ubuntu documentation for this device?

---

