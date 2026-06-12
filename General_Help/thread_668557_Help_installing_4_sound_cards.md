---
title: "Help installing 4 sound cards"
date: 2008-01-15
forum: General Help
---

### Post by never-enuff on 2008-01-15
I am trying to install 4 sound cards on Ubuntu 7.10, ( AC97-on board, Creative Labs SB0310, Soundblaster Live CT4780 and Ensoniq ES1370) I had 3 of them working after a fresh install and somehow while trying to get the forth to work, I lost all of them.  Could someone please help guide me in the direction to get them all installed and working.

what other information is needed?

lspci: 
------
00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

aplay -l:
----------
**** List of PLAYBACK Hardware Devices ****
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lsmod:
--------
Module                  Size  Used by
savage                 34048  2
drm                    83476  3 savage
ipv6                  278916  12
lp                     12452  0
loop                   19076  0
snd_via82xx            29464  0
gameport               16776  1 snd_via82xx
snd_ac97_codec        100260  1 snd_via82xx
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11528  2 snd_via82xx,snd_pcm
snd_mpu401_uart         9600  1 snd_via82xx
snd_seq_dummy           4740  0
snd_seq_oss            33152  0
snd_seq_midi            9600  0
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53104  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54532  11 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
parport_pc             37668  1
parport                37448  2 lp,parport_pc
pcspkr                  4224  0
via_ircc               27924  0
i2c_prosavage           5248  0
psmouse                39952  0
serio_raw               8068  0
irda                  202300  1 via_ircc
i2c_algo_bit            7428  1 i2c_prosavage
crc_ccitt               3072  1 irda
i2c_viapro             10132  0
i2c_core               26112  3 i2c_prosavage,i2c_algo_bit,i2c_viapro
via_agp                11264  1
agpgart                35144  2 drm,via_agp
shpchp                 34580  0
pci_hotplug            32576  1 shpchp
af_packet              24840  2
evdev                  11136  1
ext3                  133640  1
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_cd                 32416  0
cdrom                  37408  1 ide_cd
ide_disk               18432  3
via82cxxx              10244  0 [permanent]
ide_core              116932  3 ide_cd,ide_disk,via82cxxx
floppy                 59876  0
ata_generic             8580  0
libata                125168  1 ata_generic
scsi_mod              146828  1 libata
ehci_hcd               36748  0
uhci_hcd               26640  0
usbcore               138760  3 ehci_hcd,uhci_hcd
8139too                27776  0
8139cp                 25344  0
mii                     6656  2 8139too,8139cp
thermal                14344  0
processor              32072  1 thermal
fan                     5764  0
fuse                   47124  1
apparmor               40600  0
commoncap               8320  1 apparmor

Thnx

Dickie

---

