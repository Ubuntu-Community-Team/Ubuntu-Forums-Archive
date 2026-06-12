---
title: "TV doesn't works :("
date: 2004-10-29
forum: General Help
---

### Post by mrchocobo on 2004-10-29
i have an AVerMedia TV card that worked in mandrake or knoppix but i can't get it to work with ubuntu :(


this is the output for lsmod:

Module                  Size  Used by
proc_intf               3968  0
freq_table              4356  0
cpufreq_userspace       5336  0
cpufreq_powersave       2048  0
button                  6936  0
ac                      5132  0
battery                 9740  0
ipv6                  230020  8
af_packet              20872  2
snd_ens1371            23012  3
snd_rawmidi            23232  1 snd_ens1371
snd_seq_device          7944  1 snd_rawmidi
snd_ac97_codec         59268  1 snd_ens1371
gameport                4736  1 snd_ens1371
8139too                23936  0
8139cp                 19072  0
snd_bt87x              13640  0
snd_pcm_oss            48168  0
snd_mixer_oss          16640  3 snd_pcm_oss
snd_pcm                85540  3 snd_ens1371,snd_bt87x,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd                    50660  11 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97 _codec,snd_bt87x,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         11144  2 snd_bt87x,snd_pcm
bt878                  11184  0
tuner                  18448  0
tvaudio                20620  0
bttv                  143020  1 bt878
video_buf              20356  1 bttv
i2c_algo_bit            8968  1 bttv
v4l2_common             6400  1 bttv
btcx_risc               4744  1 bttv
i2c_core               22416  4 tuner,tvaudio,bttv,i2c_algo_bit
videodev                9856  1 bttv
soundcore               9824  4 snd,bttv
stir4200               13700  0
irda                  167360  1 stir4200
crc_ccitt               2432  1 irda
uhci_hcd               29328  0
pci_hotplug            30640  0
amd_k7_agp              7692  1
agpgart                31784  1 amd_k7_agp
floppy                 54996  0
pcspkr                  3816  0
rtc                    12216  0
nls_iso8859_1           4352  1
nls_cp437               6016  1
vfat                   13312  1
fat                    41792  1 vfat
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
usbnet                 25352  0
usbcore               104292  5 stir4200,uhci_hcd,usbnet
mii                     4864  3 8139too,8139cp,usbnet
crc32                   4608  4 8139too,8139cp,stir4200,usbnet
parport_pc             32064  1
lp                     10436  0
parport                37320  2 parport_pc,lp
ide_cd                 38276  0
cdrom                  35872  1 ide_cd
tsdev                   7168  0
evdev                   9088  0
mousedev               10124  1
psmouse                17800  0
ext3                  109544  1
jbd                    54552  1 ext3
ide_generic             1664  0
via82cxxx              13084  1
pdc202xx_old           15516  1
ide_disk               16768  4
ide_core              125272  5 ide_cd,ide_generic,via82cxxx,pdc202xx_old,ide_di sk
unix                   25904  668
fan                     4236  0
thermal                13200  0
processor              17712  1 thermal
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb





and this one the output for lspci

0000:00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-760 [IGD4-1P] System Controller (rev 13)
0000:00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-760 [IGD4-1P] AGP Bridge
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
0000:00:09.0 VGA compatible controller: nVidia Corporation NV4 [RIVA TNT] (rev 04)
0000:00:0a.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:00:0a.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
0000:00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:0e.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 03)
0000:00:10.0 Unknown mass storage controller: Promise Technology, Inc. 20265 (rev 02)




and dmesg

Linux video capture interface: v1.00
bttv: driver version 0.9.15 loaded
bttv: using 8 buffers with 2080k (520 pages) each for capture
bttv: Bt8xx card found (0).
ACPI: PCI interrupt 0000:00:0a.0[A] -> GSI 5 (level, low) -> IRQ 5
bttv0: Bt878 (rev 17) at 0000:00:0a.0, irq: 5, latency: 32, mmio: 0xd7020000
bttv0: detected: AVerMedia TVCapture 98 [card=13], PCI subsystem ID is 1461:0004
bttv0: using: AVerMedia TVCapture 98 [card=13,autodetected]
bttv0: gpio: en=00000000, out=00000000 in=00847ff3 [init]
bttv0: Hauppauge/Voodoo msp34xx: reset line init [11]
bttv0: Avermedia eeprom[0x0afc]: tuner=Unknown type radio:yes remote control:no
bttv0: using tuner=5
bttv0: i2c: checking for MSP34xx @ 0x80... not found
bttv0: i2c: checking for MSP34xx (alternate address) @ 0x88... not found
bttv0: i2c: checking for TDA9875 @ 0xb0... not found
bttv0: i2c: checking for TDA7432 @ 0x8a... not found
tvaudio: TV audio decoder + audio/video mux driver
tvaudio: known chips: tda9840,tda9873h,tda9874h/a,tda9850,tda9855,tea6300,tea6420,tda8425,pic16c54 (PV951),ta8874z
tuner: chip found at addr 0xc2 i2c-bus bt878 #0 [sw]
tuner: type set to 5 (Philips PAL_BG (FI1216 and compatibles)) by bt878 #0 [sw]
bttv0: registered device video0
bttv0: registered device vbi0
bttv0: PLL: 28636363 => 35468950 .. ok
bt878: AUDIO driver version 0.0.0 loaded
bt878: Bt878 AUDIO function found (0).


so from dmesg it seems to have detected the card, and all seems to be right 

but if i try scantv with pal as tv norm and europe-west as frequency table, as i'm from spain, i get 

vbi: open failed [/dev/vbi]
open /dev/vbi: No such file or directory
 


so i tried "ln -s /dev/vbi0 /dev/vbi", and then if i try to scan the channels, for all of them it says "no station", as if it wouldn't be able to get any signal

anybody knows what can i try? cause all seems to be right to me :(

---

### Post by manwy on 2005-02-26
[QUOTE=mrchocobo]i have an AVerMedia TV card that worked in mandrake or knoppix but i can't get it to work with ubuntu :(


this is the output for lsmod:

Module                  Size  Used by
proc_intf               3968  0
freq_table              4356  0
cpufreq_userspace       5336  0
cpufreq_powersave       2048  0
button                  6936  0
ac                      5132  0
battery                 9740  0
ipv6                  230020  8
af_packet              20872  2
snd_ens1371            23012  3
snd_rawmidi            23232  1 snd_ens1371
snd_seq_device          7944  1 snd_rawmidi
snd_ac97_codec         59268  1 snd_ens1371
gameport                4736  1 snd_ens1371
8139too                23936  0
8139cp                 19072  0
snd_bt87x              13640  0
snd_pcm_oss            48168  0
snd_mixer_oss          16640  3 snd_pcm_oss
snd_pcm                85540  3 snd_ens1371,snd_bt87x,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd                    50660  11 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97 _codec,snd_bt87x,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         11144  2 snd_bt87x,snd_pcm
bt878                  11184  0
tuner                  18448  0
tvaudio                20620  0
bttv                  143020  1 bt878
video_buf              20356  1 bttv
i2c_algo_bit            8968  1 bttv
v4l2_common             6400  1 bttv
btcx_risc               4744  1 bttv
i2c_core               22416  4 tuner,tvaudio,bttv,i2c_algo_bit
videodev                9856  1 bttv
soundcore               9824  4 snd,bttv
stir4200               13700  0
irda                  167360  1 stir4200
crc_ccitt               2432  1 irda
uhci_hcd               29328  0
pci_hotplug            30640  0
amd_k7_agp              7692  1
agpgart                31784  1 amd_k7_agp
floppy                 54996  0
pcspkr                  3816  0
rtc                    12216  0
nls_iso8859_1           4352  1
nls_cp437               6016  1
vfat                   13312  1
fat                    41792  1 vfat
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
usbnet                 25352  0
usbcore               104292  5 stir4200,uhci_hcd,usbnet
mii                     4864  3 8139too,8139cp,usbnet
crc32                   4608  4 8139too,8139cp,stir4200,usbnet
parport_pc             32064  1
lp                     10436  0
parport                37320  2 parport_pc,lp
ide_cd                 38276  0
cdrom                  35872  1 ide_cd
tsdev                   7168  0
evdev                   9088  0
mousedev               10124  1
psmouse                17800  0
ext3                  109544  1
jbd                    54552  1 ext3
ide_generic             1664  0
via82cxxx              13084  1
pdc202xx_old           15516  1
ide_disk               16768  4
ide_core              125272  5 ide_cd,ide_generic,via82cxxx,pdc202xx_old,ide_di sk
unix                   25904  668
fan                     4236  0
thermal                13200  0
processor              17712  1 thermal
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb





and this one the output for lspci

0000:00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-760 [IGD4-1P] System Controller (rev 13)
0000:00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-760 [IGD4-1P] AGP Bridge
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
0000:00:09.0 VGA compatible controller: nVidia Corporation NV4 [RIVA TNT] (rev 04)
0000:00:0a.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:00:0a.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
0000:00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:0e.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 03)
0000:00:10.0 Unknown mass storage controller: Promise Technology, Inc. 20265 (rev 02)




and dmesg

Linux video capture interface: v1.00
bttv: driver version 0.9.15 loaded
bttv: using 8 buffers with 2080k (520 pages) each for capture
bttv: Bt8xx card found (0).
ACPI: PCI interrupt 0000:00:0a.0[A] -> GSI 5 (level, low) -> IRQ 5
bttv0: Bt878 (rev 17) at 0000:00:0a.0, irq: 5, latency: 32, mmio: 0xd7020000
bttv0: detected: AVerMedia TVCapture 98 [card=13], PCI subsystem ID is 1461:0004
bttv0: using: AVerMedia TVCapture 98 [card=13,autodetected]
bttv0: gpio: en=00000000, out=00000000 in=00847ff3 [init]
bttv0: Hauppauge/Voodoo msp34xx: reset line init [11]
bttv0: Avermedia eeprom[0x0afc]: tuner=Unknown type radio:yes remote control:no
bttv0: using tuner=5
bttv0: i2c: checking for MSP34xx @ 0x80... not found
bttv0: i2c: checking for MSP34xx (alternate address) @ 0x88... not found
bttv0: i2c: checking for TDA9875 @ 0xb0... not found
bttv0: i2c: checking for TDA7432 @ 0x8a... not found
tvaudio: TV audio decoder + audio/video mux driver
tvaudio: known chips: tda9840,tda9873h,tda9874h/a,tda9850,tda9855,tea6300,tea6420,tda8425,pic16c54 (PV951),ta8874z
tuner: chip found at addr 0xc2 i2c-bus bt878 #0 [sw]
tuner: type set to 5 (Philips PAL_BG (FI1216 and compatibles)) by bt878 #0 [sw]
bttv0: registered device video0
bttv0: registered device vbi0
bttv0: PLL: 28636363 => 35468950 .. ok
bt878: AUDIO driver version 0.0.0 loaded
bt878: Bt878 AUDIO function found (0).


so from dmesg it seems to have detected the card, and all seems to be right 

but if i try scantv with pal as tv norm and europe-west as frequency table, as i'm from spain, i get 

vbi: open failed [/dev/vbi]
open /dev/vbi: No such file or directory
 


so i tried "ln -s /dev/vbi0 /dev/vbi", and then if i try to scan the channels, for all of them it says "no station", as if it wouldn't be able to get any signal

anybody knows what can i try? cause all seems to be right to me :([/QUOTE]
 I have the same problem. Please help!!!

---

### Post by illek on 2005-02-26
Are you using xawtv?  This is the only program I could get my Avermedia car to work under.

---

