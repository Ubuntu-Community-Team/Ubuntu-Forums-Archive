---
title: "sound won't work on either gibbons of fawn"
date: 2007-11-29
forum: General Help
---

### Post by Larsburham on 2007-11-29
I tried the official troubleshooter my card is recognized by the OS, i loaded the drivers, but it cannot be used in any program. What do i do now?

Here is my lspci

00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev 23)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 11)
00:07.3 Host bridge: VIA Technologies, Inc. VT82C596 Power Management (rev 30)
00:0e.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08)
00:10.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
00:12.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 74)


Here is my aplay -l 

**** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by linuxwizard on 2007-11-30
When posting try to give as much info as you can. Computer specs what sound card are you using. What have you done so far trying to get it to work. Maybe someone can help you than.

---

### Post by EWAERBL on 2007-11-30
ok, here goes.  i'm running ubuntu 7.1, upgraded from 7.04 .  my system sounds dont work.     the sound card is an old es1370 (equisonic).  amd athlon 64 3000+   when i go to system/pref/sound, i can get a tone in sound events usind es1370 dac1 and music & movies as well as audio conf.  but when i click over to the sounds tab none of them work.  are there sound levels to turn up somewheres else like in windows?  the sound level on the desktop is turned all the way up .  i get really loud tones!

---

