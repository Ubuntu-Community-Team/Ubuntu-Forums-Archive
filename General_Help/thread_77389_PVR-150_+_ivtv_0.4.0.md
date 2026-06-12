---
title: "PVR-150 + ivtv 0.4.0"
date: 2005-10-16
forum: General Help
---

### Post by triplep on 2005-10-16
Hey, I'm quite new to Ubuntu (<3 days) and I'm really enjoying it so far. However, I am having a major issue with a PVR-150 card and ivtv0.4.0 not loading the firmware.

[4298141.130000] ivtv:  ==================== START INIT IVTV ====================
[4298141.130000] ivtv:  version 0.4.0 (tagged release) loading
[4298141.130000] ivtv:  Linux version: 2.6.12-9-386 386 gcc-3.4
[4298141.130000] ivtv:  In case of problems please include the debug info
[4298141.130000] ivtv:  between the START INIT IVTV and END INIT IVTV lines when
[4298141.130000] ivtv:  mailing the ivtv-devel mailinglist.
[4298141.136000] ivtv0: Autodetected WinTV PVR 150 card (iTVC16 based)
[4298141.136000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 17 (level, low) -> IRQ 17
[4298141.226000] tveeprom: The eeprom says no radio is present, but the tuner type 68
[4298141.226000] tveeprom: indicates otherwise. I will assume that radio is present.
[4298141.226000] tveeprom: ivtv version
[4298141.226000] tveeprom: Hauppauge: model = 26552, rev = C268, serial# = 2987242
[4298141.226000] tveeprom: tuner = LG TAPE H001F MK3 (idx = 68, type = 47)
[4298141.226000] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000)
[4298141.226000] tveeprom: audio processor = CX25843 (type = 25)
[4298141.226000] tveeprom: decoder processor = CX25843 (type = 1e)
[4298141.226000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[4298141.258000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[4298141.258000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[4298141.313000] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[4298142.700000] cx25840 1-0044: loaded /lib/modules/HcwMakoA.ROM firmware (14264 bytes)
[4298142.776000] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[4298142.790000] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
[4298142.801000] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[4298142.817000] tda9885/6/7: (ivtv) chip found @ 0x86
[4298142.817000] ivtv0: i2c attach to card #0 ok [client=tda9887, addr=43]
[4298143.431000] ivtv0: loading /lib/modules/ivtv-fw-enc.bin
[4298143.431000] ivtv0: unable to open firmware
[4298143.431000] ivtv0 warning: failed loading encoder firmware
[4298143.431000] ivtv0 warning: Error loading firmware -3!
[4298143.431000] ivtv0: Error -3 initializing firmware.
[4298143.441000] ivtv0: Error -12 on initialization
[4298143.441000] ivtv-iTVC15_16_mpg2_encoder_card: probe of 0000:00:0c.0 failed with error -12
[4298143.441000] ivtv0: Autodetected WinTV PVR 150 card (iTVC16 based)
[4298143.441000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 19 (level, low) -> IRQ 19
[4298143.505000] tveeprom: ivtv version
[4298143.505000] tveeprom: Hauppauge: model = 26032, rev = C199, serial# = 8208856
[4298143.505000] tveeprom: tuner = TCL 2002N 5H (idx = 99, type = 50)
[4298143.505000] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000)
[4298143.505000] tveeprom: audio processor = CX25841 (type = 23)
[4298143.505000] tveeprom: decoder processor = CX25841 (type = 1c)
[4298143.505000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[4298143.510000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[4298143.510000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[4298143.535000] cx25840 1-0044: cx25841-23 found @ 0x88 (ivtv i2c driver #0)
[4298144.862000] cx25840 1-0044: loaded /lib/modules/HcwMakoA.ROM firmware (14264 bytes)
[4298144.937000] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[4298144.944000] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
[4298144.954000] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[4298145.647000] ivtv0: loading /lib/modules/ivtv-fw-enc.bin
[4298145.647000] ivtv0: unable to open firmware
[4298145.647000] ivtv0 warning: failed loading encoder firmware
[4298145.647000] ivtv0 warning: Error loading firmware -3!
[4298145.647000] ivtv0: Error -3 initializing firmware.
[4298145.709000] ivtv0: Error -12 on initialization
[4298145.709000] ivtv-iTVC15_16_mpg2_encoder_card: probe of 0000:00:0e.0 failed with error -12
[4298145.709000] ivtv:  ====================  END INIT IVTV  ====================


I've been using the guide at [http://www.slash32.com/ubuntu-myth.html](http://www.slash32.com/ubuntu-myth.html) which is for a pvr-250, so it's a little different, instead, I need to use different firmware drivers, which is indicated at [http://ivtvdriver.org/index.php/Firmware#Firmware_Checksums](http://ivtvdriver.org/index.php/Firmware#Firmware_Checksums)  which points me to the firmware at [ftp://ftp.shspvr.com/download/wintv-pvr_150-500/inf/pvr_2.0.24.23035.zip](ftp://ftp.shspvr.com/download/wintv-pvr_150-500/inf/pvr_2.0.24.23035.zip)

"Unzip it and copy HcwMakoA.ROM to /lib/modules/. Also copy HcwFalcn.rom to /lib/modules/ivtv-fw-enc.bin. " is being done, and all that stuff ends up in /lib/modules.

Has anyone had issues with this problem? Any help or insight would be most appreciated.

Worst part of it is that I had this working in amd64 yesterday and moved to 386 for the better support of mythtv....

---

### Post by Ronbo on 2005-10-16
This link for the MythTV HOWTO was posted in another thread, This was written specifically for Ubuntu. This is the capture card section:

[http://www.abarbaccia.com/content/view/19/29/]("http://www.abarbaccia.com/content/view/19/29/")

This is the thread I got it from:

[http://www.ubuntuforums.org/showthread.php?t=29510&highlight=abarbaccia.com]("http://www.ubuntuforums.org/showthread.php?t=29510&highlight=abarbaccia.com")

I am planning to give it a shot myself so I've been going over the HOWTO.  Hope this helps.  I'm kinda new to this myself.

---

### Post by triplep on 2005-10-16
Thanks Ronbo, I've already used both of these sights as resources, however I starting to feel more like starting fresh using the Abarbacbia guide.

Anyone else running ivtv0.40 with a pvr 150 out there? i just want to know that you exist....

---

### Post by triplep on 2005-10-16
if you have this problem...... do

'sudo reboot'

looked at dmesg on the reboot, both cards loaded nicely, 150 OEM and 150 MCE

[4294690.903000] ivtv:  ==================== START INIT IVTV =================== =
[4294690.903000] ivtv:  version 0.4.0 (tagged release) loading
[4294690.903000] ivtv:  Linux version: 2.6.12-9-386 386 gcc-3.4
[4294690.903000] ivtv:  In case of problems please include the debug info
[4294690.903000] ivtv:  between the START INIT IVTV and END INIT IVTV lines when
[4294690.903000] ivtv:  mailing the ivtv-devel mailinglist.
[4294690.923000] ivtv0: Autodetected WinTV PVR 150 card (iTVC16 based)
[4294690.923000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 17 (level, low) -> I RQ 17
[4294690.995000] tveeprom: The eeprom says no radio is present, but the tuner ty pe 68
[4294690.995000] tveeprom: indicates otherwise. I will assume that radio is pres ent.
[4294690.995000] tveeprom: ivtv version
[4294690.995000] tveeprom: Hauppauge: model = 26552, rev = C268, serial# = 29872 42
[4294690.995000] tveeprom: tuner = LG TAPE H001F MK3 (idx = 68, type = 47)
[4294690.995000] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000 )
[4294690.995000] tveeprom: audio processor = CX25843 (type = 25)
[4294690.995000] tveeprom: decoder processor = CX25843 (type = 1e)
[4294690.995000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[4294691.018000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver # 0
[4294691.018000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[4294691.079000] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[4294692.414000] cx25840 0-0044: loaded /lib/modules/HcwMakoA.ROM firmware (1426 4 bytes)
[4294692.489000] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[4294692.503000] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[4294692.514000] ivtv0: i2c attach to card #0 ok [client=wm8775, addr=1b]
[4294692.538000] tda9885/6/7: (ivtv) chip found @ 0x86
[4294692.538000] ivtv0: i2c attach to card #0 ok [client=tda9887, addr=43]
[4294693.224000] ivtv0: loading /lib/modules/ivtv-fw-enc.bin
[4294693.456000] ivtv0: Encoder revision: 0x02050032
[4294693.457000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4 096KB total)
[4294693.484000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (20 48KB total)
[4294693.485000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (20 48KB total)
[4294693.499000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffer s (2048KB total)
[4294693.514000] ivtv0: Create encoder radio stream
[4294693.514000] tuner: type set to 47 (LG NTSC (TAPE series)) by ivtv i2c drive r #0
[4294693.862000] ivtv0: Initialized WinTV PVR 150, card #0
[4294693.862000] ivtv:  ======================  NEXT CARD  ===================== =
[4294693.862000] ivtv1: Autodetected WinTV PVR 150 card (iTVC16 based)
[4294693.862000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 19 (level, low) -> I RQ 19
[4294693.924000] tveeprom: ivtv version
[4294693.924000] tveeprom: Hauppauge: model = 26032, rev = C199, serial# = 82088 56
[4294693.924000] tveeprom: tuner = TCL 2002N 5H (idx = 99, type = 50)
[4294693.924000] tveeprom: tuner fmt = NTSC(M) (eeprom = 0x08, v4l2 = 0x00001000 )
[4294693.924000] tveeprom: audio processor = CX25841 (type = 23)
[4294693.924000] tveeprom: decoder processor = CX25841 (type = 1c)
[4294693.924000] ivtv1: i2c attach to card #1 ok [client=tveeprom, addr=50]
[4294693.939000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver # 1
[4294693.939000] ivtv1: i2c attach to card #1 ok [client=(tuner unset), addr=61]
[4294693.974000] cx25840 1-0044: cx25841-23 found @ 0x88 (ivtv i2c driver #1)
[4294695.225000] cx25840 1-0044: loaded /lib/modules/HcwMakoA.ROM firmware (1426 4 bytes)
[4294695.300000] ivtv1: i2c attach to card #1 ok [client=cx25840, addr=44]
[4294695.304000] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #1)
[4294695.314000] ivtv1: i2c attach to card #1 ok [client=wm8775, addr=1b]
[4294695.989000] ivtv1: loading /lib/modules/ivtv-fw-enc.bin
[4294696.201000] ivtv1: Encoder revision: 0x02050032
[4294696.202000] ivtv1: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4 096KB total)
[4294696.216000] ivtv1: Allocate DMA encoder YUV stream: 194 x 10800 buffers (20 48KB total)
[4294696.230000] ivtv1: Allocate DMA encoder VBI stream: 120 x 17472 buffers (20 48KB total)
[4294696.244000] ivtv1: Allocate DMA encoder PCM audio stream: 455 x 4608 buffer s (2048KB total)
[4294696.245000] tuner: type set to 50 (TCL 2002N) by ivtv i2c driver #1
[4294696.582000] ivtv1: Initialized WinTV PVR 150, card #1
[4294696.582000] ivtv:  ====================  END INIT IVTV  =================== 


i thought linux rebooting was for adding new hardware, not making the hardware actually work ;)

---

