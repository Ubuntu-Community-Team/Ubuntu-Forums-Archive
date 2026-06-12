---
title: "&quot;Error: InitializeInputs()&quot; when starting mythbackend"
date: 2006-11-02
forum: General Help
---

### Post by Nomad64 on 2006-11-02
I have searched the forums and haven't been able to find an answer to this problem. Basically, I installed MythTV using [https://wiki.ubuntu.com/Install_IVTV_Edgy]("this guide") and I didn't notice any critical error messages while going through it. I also ran "dmesg" and it shows that IVTV is correctly initialized:```
[17179598.732000] ivtv:  ==================== START INIT IVTV ====================
[17179598.732000] ivtv:  version 0.7.0 (tagged release) loading
[17179598.732000] ivtv:  Linux version: 2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
[17179598.732000] ivtv:  In case of problems please include the debug info between
[17179598.732000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[17179598.732000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[17179599.220000] ivtv0: Autodetected Hauppauge WinTV PVR-150 card (cx23416 based)
[17179599.220000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[17179599.292000] tveeprom 1-0050: Hauppauge model 23552, rev D492, serial# 9492515
[17179599.292000] tveeprom 1-0050: tuner model is Philips FQ1236A MK4 (idx 92, type 57)
[17179599.292000] tveeprom 1-0050: TV standards NTSC(M) (eeprom 0x08)
[17179599.292000] tveeprom 1-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[17179599.292000] tveeprom 1-0050: audio processor is CX25843 (idx 37)
[17179599.292000] tveeprom 1-0050: decoder processor is CX25843 (idx 30)
[17179599.292000] tveeprom 1-0050: has radio, has no IR remote
[17179599.292000] ivtv0: This is the first unit of a PVR500
[17179599.404000] tuner 1-0060: TEA5767 detected.
[17179599.404000] tuner 1-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[17179599.404000] tuner 1-0060: type set to 62 (Philips TEA5767HN FM Radio)
[17179599.404000] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[17179599.560000] NET: Registered protocol family 17
[17179599.612000] tda9887 1-0043: chip found @ 0x86 (ivtv i2c driver #0)
[17179599.780000] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[17179599.960000] floppy0: no floppy controllers found
[17179600.176000] NET: Registered protocol family 10
[17179600.176000] lo: Disabled Privacy Extensions
[17179600.176000] IPv6 over IPv4 tunneling driver
[17179601.296000] 0000:00:11.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[17179601.296000] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
[17179603.284000] cx25840 1-0044: loaded v4l-cx25840.fw firmware (14264 bytes)
[17179603.420000] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
[17179604.140000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[17179604.356000] ivtv0: Encoder revision: 0x02050032
[17179604.356000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[17179604.356000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[17179604.356000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[17179604.356000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[17179604.360000] ivtv0: Create encoder radio stream
[17179604.360000] tuner 1-0061: type set to 57 (Philips FQ1236A MK4)
[17179604.484000] ivtv0: Initialized WinTV PVR 500 (unit #1), card #0
[17179604.484000] ivtv:  ======================  NEXT CARD  ======================
[17179604.484000] ivtv1: Autodetected Hauppauge WinTV PVR-150 card (cx23416 based)
[17179604.484000] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [LNKA] -> GSI 5 (level, low) -> IRQ 5
[17179604.536000] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[17179604.696000] tda9887 2-0043: chip found @ 0x86 (ivtv i2c driver #1)
[17179604.712000] cx25840 2-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #1)
[17179607.720000] cx25840 2-0044: loaded v4l-cx25840.fw firmware (14264 bytes)
[17179607.796000] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #1)
[17179607.880000] tveeprom 2-0050: Hauppauge model 23552, rev D492, serial# 9492515
[17179607.880000] tveeprom 2-0050: tuner model is Philips FQ1236A MK4 (idx 92, type 57)
[17179607.880000] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[17179607.880000] tveeprom 2-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[17179607.880000] tveeprom 2-0050: audio processor is CX25843 (idx 37)
[17179607.880000] tveeprom 2-0050: decoder processor is CX25843 (idx 30)
[17179607.880000] tveeprom 2-0050: has radio, has no IR remote
[17179607.880000] ivtv1: This is the second unit of a PVR500
[17179607.880000] ivtv1: Correcting tveeprom data: no radio present on second unit
[17179608.728000] ivtv1: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[17179608.944000] ivtv1: Encoder revision: 0x02050032
[17179608.944000] ivtv1: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[17179608.944000] ivtv1: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[17179608.944000] ivtv1: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[17179608.948000] ivtv1: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[17179608.948000] tuner 2-0061: type set to 57 (Philips FQ1236A MK4)
[17179609.068000] ivtv1: Initialized WinTV PVR 500 (unit #2), card #1
[17179609.068000] ivtv:  ====================  END INIT IVTV  ====================
```
But when I run mythbackend, it returns this error:```
$ sudo mythbackend
2006-11-02 08:40:38.998 Using runtime prefix = /usr
2006-11-02 08:40:39.087 New DB connection, total: 1
2006-11-02 08:40:39.109 Connected to database 'mythconverg' at host: localhost
2006-11-02 08:40:39.121 Current Schema Version: 1160
Starting up as the master server.
2006-11-02 08:40:39.144 New DB connection, total: 2
2006-11-02 08:40:39.146 Connected to database 'mythconverg' at host: localhost
2006-11-02 08:40:39.152 EITHelper: localtime offset -6:00:00
2006-11-02 08:40:39.162 TVRec(1) Error: Problem finding starting channel, setting to default of '3'.
2006-11-02 08:40:39.165 ChannelBase(1) Error: InitializeInputs():
                        Could not get inputs for the capturecard.
                        Perhaps you have forgotten to bind video
                        sources to your card's inputs?
2006-11-02 08:40:39.168 EITHelper: localtime offset -6:00:00
2006-11-02 08:40:39.173 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2006-11-02 08:40:39.174 ChannelBase(2) Error: InitializeInputs():
                        Could not get inputs for the capturecard.
                        Perhaps you have forgotten to bind video
                        sources to your card's inputs?
```

Does anyone have any idea how to fix this?

---

### Post by Nomad64 on 2006-11-04
*bump*

I tried installing from source using [this guide]("http://www.mythtv.org/wiki/index.php/Ubuntu_Edgy_Installation_From_Source") and still get the same errors.

I am pretty sure the IVTV drivers are installed properly, since the MythTV setup program is able to detect them...but the backend still refuses to load.

I am seriously considering just reinstalling Dapper, since I know MythTV works with it.

---

### Post by superm1 on 2006-11-05
You have run mythtv-setup prior to starting the backend, correct?

---

### Post by bvidinli on 2008-05-03
i have same issue:

here is error on logs:

2008-05-04 00:55:52.795 TVRec(1) Error: Problem finding starting channel, setting to default of '3'.
2008-05-04 00:55:52.798 ChannelBase(1) Error: InitializeInputs(): 
			Could not get inputs for the capturecard.
			Perhaps you have forgotten to bind video
			sources to your card's inputs?
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?


do you have any idea ?
thanks

---

### Post by karlec on 2008-05-04
I have the same problem, one of my PVR500 inputs is showing as being unavailable on the status page in mythfrontend and the logs are showing the same message as above.

---

