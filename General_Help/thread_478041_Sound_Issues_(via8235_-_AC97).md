---
title: "Sound Issues (via8235 - AC97)"
date: 2007-06-18
forum: General Help
---

### Post by Ptero-4 on 2007-06-18
Hi. A relative of mine decided to switch to linux (kubuntu dapper) from WinXP but his soundcard doesn't seem to work at all on ubuntu. His computer specs are:
AMD AthlonXP 2.4GHz
NVidia GeForce4 MX420
512MB RAM
80GB HD
DVDROM
CDRW
AC97 sound
Agere Systems LT Winmodem
Realtek NIC

here's the lspci:
```

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
0000:00:09.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 05)
0000:00:0a.0 Communication controller: Agere Systems LT WinModem (rev 02)
0000:00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)

```

The aplay -l:
```

**** Lista de PLAYBACK Dispositivos Hardware ****
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
And finally a screenshot of Kinfocenter.

---

### Post by Azakus on 2007-06-19
Hmm. Sometimes on a fresh install, the default volume will be set to zero. Try running "alsamixer" and raising all the volume levels to the maximum.

---

### Post by Ptero-4 on 2007-06-19
I tried that already, still no sound.

---

### Post by Azakus on 2007-06-20
Your relative is using dapper? Try upgrading to feisty. Much better hardware support.
Also, try this list:
[Comprehensive Sound Problem Solutions Guide v0.5e](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by _duncan_ on 2007-06-20
One of my ubuntu boxes has a similar spec:

```
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
```

With Breezy 5.10 and Dapper 6.06, I had to play around with the alsamixer controls to get sound working.

However starting with Edgy 6.10 and now Feisty 7.04, sound works out of the box for me.

---

### Post by Ptero-4 on 2007-06-21
My relative's is rev 50 IIRC.

---

