---
title: "Tv-tuner issues"
date: 2006-10-12
forum: General Help
---

### Post by lesemi on 2006-10-12
I've searched several threads for some help on the driver saa7134.
still can't make my tv-tuner work at all.

On ubuntu dapper the driver recognized the card - i did tvtime scanner and it picked up the analog signals - however tvtime was all disorted - 

i'm on kubuntu dapper now - and the driver doesn't pick up the card - i've exausted all my knowledge on this.  Any help would be helpful.

i have a sabrent tvtuner card with the philips chip saa713

here's my dmesg | grep saa

[17179590.696000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17179590.968000] saa7130[0]: found at 0000:05:06.0, rev: 1, irq: 58, latency: 32, mmio: 0xd3010000
[17179590.968000] saa7130[0]: subsystem: 1131:0000, board: Sabrent SBT-TVFM (saa7130) [card=42,insmod option]
[17179590.968000] saa7130[0]: board init: gpio is 80c000
[17179591.072000] saa7130[0]: Huh, no eeprom present (err=-5)?
[17179591.116000] tuner 2-0060: chip found @ 0xc0 (saa7130[0])
[17179591.300000] tuner 2-0061: chip found @ 0xc2 (saa7130[0])
[17179591.316000] saa7130[0]: registered device video0 [v4l2]
[17179591.316000] saa7130[0]: registered device vbi0
[17179591.316000] saa7130[0]: registered device radio0
[17179591.328000] saa7134 ALSA driver for DMA sound loaded
[17179591.328000] saa7130[0]/alsa: saa7130[0] at 0xd3010000 irq 58 registered as card -1

any ideas?

---

### Post by fragos on 2006-10-12
At times, Linux will recognize the TV chip set but not the tuner.  There's only a few TV chip sets but over 50 tuners which can be swaped by manufacturers without changes in card model.  If this is the case Linux will set your tuner to 0.  My hardware is different but here's an example of a working tuner configuration.

fragos@Geo:~$ dmesg|grep tuner
[17179588.228000] tveeprom 0-0050: tuner model is LG TAPC H791F (idx 82, type 39)
[17179588.228000] bttv0: using tuner=39
[17179588.320000] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[17179588.320000] tuner 0-0061: type set to 39 (LG NTSC (newer TAPC series))

---

### Post by lesemi on 2006-10-13
Hi,

you seem to have the bttv chip  -  i'm not sure if the drivers behave differently.

Should i add the line:
saa7134: using tuner=xx?
instead of:
[17179588.228000] bttv0: using tuner=39

as well - some threads were discussing adding a line in 
/etc/modprobe.conf:
'options saa7134 card=42 tuner=58'
that didn't work either- 

I manually tried everytuner one by one in modprobe.conf - and that didn't work - however i didn't reboot in between - i'm not that patient ;) 

any ideas?  ](*,)

---

### Post by fragos on 2006-10-13
The lines I showed were the output of the command "dmesg|grep tuner" and the purpose was to show you a working example even if for a differrent chip set.  I was hoping that seeing the working system output would help you interpret what you have, particularly to identify what tuner is identified.  I've only had successsful experience with the bttv driver.  I also have a PVR card which requires the ivtv driver but I've yet to be able to get it functioning.  I decided to wait on it until the driver is better integrated into Linux like the bttv diver has been.

---

