---
title: "Remote not Working in Feisty"
date: 2007-06-21
forum: General Help
---

### Post by paulngwen on 2007-06-21
I have MythTV installed on Fiesty and everything is working except the remote.  The card is working properly to record and everything works in MythTV but the remote just gets no response at all.  I've searched the ubuntuforums.org and ubuntu help and found several similar problems but none of their fixes have made a dent - still no response from the remote.  When using the irw command there is nothing that happens at all on the screen.  Any help to point me in the right direction would be greatly appreciated.  I've only been working with Ubuntu for about two months now so I am still a newbie.  My apologies if this is posted in the wrong place.  Thanks for any help anyone can provide.  Attached is the IVTV part of the dmesg response.



[   22.008000] ivtv:  ==================== START INIT IVTV ====================
[   22.008000] ivtv:  version 0.10.1 (tagged release) loading
[   22.008000] ivtv:  Linux version: 2.6.20-16-generic SMP mod_unload 586 
[   22.008000] ivtv:  In case of problems please include the debug info between
[   22.008000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   22.008000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   22.008000] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   22.008000] PCI: Enabling device 0000:00:0f.0 (0014 -> 0016)
[   22.008000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LNKC] -> GSI 3 (level, low) -> IRQ 3
[   22.008000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   22.120000] input: PC Speaker as /class/input/input2
[   22.608000] logips2pp: Detected unknown logitech mouse model 127
[   22.720000] nvidia: module license 'NVIDIA' taints kernel.
[   23.072000] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input3
[   23.744000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   23.960000] ivtv0: Encoder revision: 0x02050032
[   23.960000] ivtv0: Recommended firmware version is 0x02060039.
[   24.044000] tveeprom 0-0050: Hauppauge model 32062, rev B185, serial# 2869305
[   24.044000] tveeprom 0-0050: tuner model is TCL 2002N 6A (idx 85, type 50)
[   24.044000] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   24.044000] tveeprom 0-0050: audio processor is MSP3445 (idx 12)
[   24.044000] tveeprom 0-0050: decoder processor is SAA7115 (idx 19)
[   24.044000] tveeprom 0-0050: has no radio, has IR receiver, has no IR transmitter
[   24.044000] ivtv0: Autodetected Hauppauge WinTV PVR-250
[   24.088000] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   24.188000] saa7115 0-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #0)
[   24.412000] msp3400 0-0040: MSP3445G-B8 found @ 0x80 (ivtv i2c driver #0)
[   24.412000] msp3400 0-0040: MSP3445G-B8 supports radio, mode is autodetect and autoselect
[   24.412000] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   24.416000] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   24.416000] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   24.416000] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   24.416000] tuner 0-0061: type set to 50 (TCL 2002N)
[   24.816000] ivtv0: Initialized Hauppauge WinTV PVR-250, card #0
[   24.816000] ivtv:  ====================  END INIT IVTV  ====================


There is also this line after the IVTV section.  Could it have anything to do with this?

[   45.836000] kobject_add failed for i2c ir driver with -EEXIST, don't try to register things with the same name in the same directory.

I don't even know where this is.

---

### Post by md2020 on 2007-08-09
> There is also this line after the IVTV section. Could it have anything to do with this?

[ 45.836000] kobject_add failed for i2c ir driver with -EEXIST, don't try to register things with the same name in the same directory.


Although this is probably too little too late, maybe it will help the next person.

This is what happens when you load both the LIRC_I2C and LIRC_PVR150 modules at the same time. (at least it happens to me) Only one of those can be loaded at a time. This is fixed by editing the /etc/lirc/hardware.conf file and removing one or the other. If you need the blaster, you need LIRC_PVR150.

Unfortunately, the instructions for installing LIRC seem to indicate that you can specify both in the hardware.conf file. From my own personal experience that is not possible. But maybe someone else can provide evidence otherwise.

---

