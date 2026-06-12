---
title: "ivtv problems"
date: 2007-05-11
forum: General Help
---

### Post by Green_Star on 2007-05-11
I have a USB webcam and PVR-150. My webcam is working by default in /dev/video0. I am not sure where my pvr-150 is running. How can I resolve. I tried all /dev/video(x) but no use. If i play /dev/video0 I can see myself from webcam. please help to resolve this. Below you can see my log. I am running UbuntuStudio.

> [   52.064487] ivtv:  ==================== START INIT IVTV ====================
[   52.064490] ivtv:  version 0.10.1 (tagged release) loading
[   52.064492] ivtv:  Linux version: 2.6.20-15-lowlatency SMP preempt mod_unload 586 
[   52.064494] ivtv:  In case of problems please include the debug info between
[   52.064495] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   52.064497] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   52.064555] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   52.095328] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   52.095337] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 21
[   52.095346] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   52.179368] usb 1-2: new full speed USB device using ohci_hcd and address 7
[   52.259509] parport: PnPBIOS parport detected.
[   52.259548] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   52.328686] irda_init()
[   52.328703] NET: Registered protocol family 23
[   52.801908] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   53.021124] ivtv0: Encoder revision: 0x02050032
[   53.021126] ivtv0: Recommended firmware version is 0x02060039.
[   53.089022] tveeprom 2-0050: Hauppauge model 26552, rev C268, serial# 8581928
[   53.089026] tveeprom 2-0050: tuner model is LG TAPE H001F MK3 (idx 68, type 47)
[   53.089028] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[   53.089030] tveeprom 2-0050: audio processor is CX25843 (idx 37)
[   53.089032] tveeprom 2-0050: decoder processor is CX25843 (idx 30)
[   53.089034] tveeprom 2-0050: has radio, has no IR receiver, has no IR transmitter
[   53.089037] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   53.114070] tuner 2-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   53.114094] tda9887 2-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   53.118584] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   53.157837] cx25840 2-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   58.176308] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   58.315862] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   58.383840] ivtv0: Registered device video1 for encoder MPEG (4 MB)
[   58.384056] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   58.384293] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   58.384442] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   58.384711] ivtv0: Registered device radio0 for encoder radio
[   58.384726] tuner 2-0061: type set to 47 (LG NTSC (TAPE series))
[   58.788834] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   58.788849] ivtv:  ====================  END INIT IVTV  ====================


---

### Post by Green_Star on 2007-05-13
I tried following

# ls /dev/video*
/dev/video0  /dev/video1  /dev/video24  /dev/video32


I tried playing video0 using VLC-Video4Linux, I am getting my webcam video. And I tried playing remaining video1, video24 and video32, got nothing.

Any clue?

---

### Post by FluffyElmo on 2007-05-13
Install ivtv-utils (*apt-get install ivtvt-utils*) and you should be able to use the ivtvctl program to investigate things. After installing just type *ivtvctl *from a terminal to see the options. Specifically, the -d switch should let you change the device used. So the following line should make the PVR-150 use /dev/video2:
```
sudo ivtvctl -d 2
```

I don't actually have my PVR-150 in my computer at the moment but I may find time to install it later if this doesn't work for you. Good luck!

---

### Post by Green_Star on 2007-05-13
wonderful, it is working when I used following command

> sudo ivtvctl -d 1

I tried with 2 as you said but it is giving following error

> $ sudo ivtvctl -d 2
Failed to open /dev/video2: No such file or directory

Anyway it is working fine in video1.

Thanks FluffyElmo.

---

