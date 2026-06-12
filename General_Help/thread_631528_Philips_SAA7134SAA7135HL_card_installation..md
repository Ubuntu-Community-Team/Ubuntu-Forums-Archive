---
title: "Philips SAA7134/SAA7135HL card installation."
date: 2007-12-04
forum: General Help
---

### Post by chiron69 on 2007-12-04
Good afternoon,  this card is driving me crazy, I can't get any image with it. I do run kubuntu gutsy

**lspci:**
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
02:01.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

jyl@jyl-desktop:~$** lsmod |grep saa**
saa7134_alsa           15392  1
snd_pcm                80388  3 snd_hda_intel,saa7134_alsa,snd_pcm_oss
saa7134               129100  1 saa7134_alsa
video_buf              26244  2 saa7134_alsa,saa7134
compat_ioctl32          2304  1 saa7134
ir_kbd_i2c              9872  1 saa7134
ir_common              35460  2 saa7134,ir_kbd_i2c
snd                    54660  14 snd_hda_intel,saa7134_alsa,snd_pcm_oss,snd_mixer_oss,snd_seq_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_core               26112  7 it87,i2c_isa,eeprom,i2c_i801,saa7134,ir_kbd_i2c,nvidia
videodev               29312  2 gspca,saa7134
v4l2_common            18432  2 saa7134,videodev
v4l1_compat            15364  2 saa7134,videodev

**dmesg**

[   41.136885] saa7130/34: v4l2 driver version 0.2.14 loaded
[   41.136953] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 19 (level, low) -> IRQ 18
[   41.136965] saa7134[0]: found at 0000:02:01.0, rev: 1, irq: 18, latency: 32, mmio: 0xf0006000
[   41.136975] saa7134[0]: subsystem: 1043:4847, board: UNKNOWN/GENERIC [card=0,autodetected]
[   41.136985] saa7134[0]: board init: gpio is 0
[   41.269847] saa7134[0]: i2c eeprom 00: 43 10 47 48 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   41.269866] saa7134[0]: i2c eeprom 10: 00 ff 82 0e ff 20 ff ff ff ff ff ff ff ff ff ff
[   41.269883] saa7134[0]: i2c eeprom 20: 01 40 01 02 03 ff 03 04 08 ff 00 2a ff ff ff ff
[   41.269901] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   41.269918] saa7134[0]: i2c eeprom 40: ff 02 00 c2 86 10 ff ff ff ff ff ff ff ff ff ff
[   41.269936] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   41.269953] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   41.269969] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   41.270105] saa7134[0]: registered device video0 [v4l2]
[   41.270152] saa7134[0]: registered device vbi0


Do anybody have an idea? Thanks

---

