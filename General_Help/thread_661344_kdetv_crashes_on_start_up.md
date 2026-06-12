---
title: "kdetv crashes on start up"
date: 2008-01-07
forum: General Help
---

### Post by cyberturtle on 2008-01-07
I have recently changed my motherboard and sound card and know when I start up kdetv I get this 

kdetv: simple.c:404: snd_mixer_selem_get_playback_switch: Assertion `(elem)->type == SND_MIXER_ELEM_SIMPLE' failed.
KCrash: Application 'kdetv' crashing...


I use a Bt878 Video capture Win Tv card that requires me to plug in the audio cable into the sound card to get audio, so I am thinking kdetv is trying to open a device that is not there and thus is crashing. I would like to change where it is looking  for the sound card. Any suggestion?
P.S. Xawtv is getting the video signal from the card just fine.

---

### Post by DaveQB on 2008-05-25
Bump on this.  Same problem here.

```

david@david ~ $ uname -a
Linux david 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux

```

```

david@david ~ $ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"


```

```

david@david ~ $ dpkg -l kdetv
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                    Version                                 Description
+++-=======================================-=======================================-==============================================================================================
ii  kdetv                                   0.8.9-1                                 TV viewer for KDE

```

---

### Post by prshah on 2008-05-25
> **DaveQB said:**
> Bump on this.  Same problem here.


Can you post the output of ```
dmesg | grep -A 5 -B 5 878
```

---

### Post by DaveQB on 2008-05-25
The modules for the card are loading fine, I added info to /etc/modprobe.d/ dir and TV time works. 

Here is the output anyway, I narrowed it down to what your after.

```

[   25.816946] bttv: driver version 0.9.17 loaded
[   25.816951] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   25.816999] bttv: Bt8xx card found (0).
[   25.817278] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 17
[   25.817288] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 17 (level, low) -> IRQ 17
[   25.817296] bttv0: Bt878 (rev 17) at 0000:01:00.0, irq: 17, latency: 128, mmio: 0xbffff000
[   25.817303] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[   25.817334] bttv0: gpio: en=00000000, out=00000000 in=00ffc0ff [init]
[   25.819479] tveeprom 2-0050: Huh, no eeprom present (err=-121)?
[   25.819483] bttv0: using tuner=-1
[   25.819485] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   25.819947] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   25.820408] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   25.820869] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   25.846911] bttv0: registered device video0
[   25.846933] bttv0: registered device vbi0
[   25.887654] bt878: AUDIO driver version 0.0.0 loaded
[   25.887694] bt878: Bt878 AUDIO function found (0).
[   25.887709] ACPI: PCI Interrupt 0000:01:00.1[A] -> Link [LNKA] -> GSI 17 (level, low) -> IRQ 17
[   25.887715] bt878_probe: card id=[0x0], Unknown card.
[   25.887715] Exiting..
[   25.887718] ACPI: PCI interrupt for device 0000:01:00.1 disabled
[   25.887722] bt878: probe of 0000:01:00.1 failed with error -22
[   26.058687] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 20
[   26.058692] ACPI: PCI Interrupt 0000:00:06.1[B] -> Link [LAZA] -> GSI 20 (level, low) -> IRQ 20
[   26.058837] PCI: Setting latency timer of device 0000:00:06.1 to 64
[   26.117386] usbcore: registered new interface driver snd-usb-audio
[   26.748474] lp: driver loaded but no devices found

```

```

[43709.843626] EXT3-fs: mounted filesystem with ordered data mode.
[45380.183556] bttv0: unloading
[45389.064966] bttv: driver version 0.9.17 loaded
[45389.064972] bttv: using 8 buffers with 2080k (520 pages) each for capture
[45389.065161] bttv: Bt8xx card found (0).
[45389.065172] bttv0: Bt878 (rev 17) at 0000:01:00.0, irq: 17, latency: 128, mmio: 0xbffff000
[45389.065295] bttv0: using: Prolink PixelView PlayTV pro [card=37,insmod option]
[45389.065323] bttv0: gpio: en=00000000, out=00000000 in=00ffc0ff [init]
[45389.066030] bttv0: using tuner=5
[45389.066072] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[45389.066578] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[45389.067097] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[45389.049941] tuner 2-0061: chip found @ 0xc2 (bt878 #0 [sw])
[45389.049980] tuner 2-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[45389.049984] tuner 2-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[45389.101531] bttv0: registered device video0
[45389.101592] bttv0: registered device vbi0
[45389.101646] bttv0: registered device radio0

```


I rmmod the module and added it again with the correct arguments, hence the 2 sections.

---

