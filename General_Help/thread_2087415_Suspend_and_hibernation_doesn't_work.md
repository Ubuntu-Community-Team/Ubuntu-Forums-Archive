---
title: "Suspend and hibernation doesn't work"
date: 2012-11-23
forum: General Help
---

### Post by firekage on 2012-11-23
Hi.

I would ask again for your help. I have problem with suspend and hibernation. They don't work, even from command line. If i run sudo pm-suspend than i see that my machine want's to shut down (suspend) but screen blinks and i see that it is not suspened, i have my desktop active.

Also the same things happens with pm-hibernation.

Only way of suspend my machine, what's is more tham strange for me, is to suspend it trough right click at the Ubuntu "logo" in right upper corner. It suspends my machine, but from the same menu hibernation doesen't work - it shuts down my machine but when i wake it up, it boots from "zero", it boots like starting machine, it's not resumed, rather its rebooted, from command line all of them (suspend, hibernation) like i said, doesn't work at all - it worked earlier.

Could you help me? I use Ubuntu 12.04, GTX260 from nVidia with 295.40 drivers (in nvidia settings **x screen display configuration **doesen't work because it says that nvidia x driver is too old to support nvidia-settings-configuration, don't know why).

Suspend and hibernation wokred before, now it doesen't and i don't know why.

Here is the output of /var/log/pm-suspend:

```

Initial commandline parameters: 
Thu Nov  1 22:16:44 CET 2012: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
decnet                 66360  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22528  5 
snd_hda_codec_via      46138  1 
ir_lirc_codec          12739  0 
tda9887                17874  1 
lirc_dev               18700  1 ir_lirc_codec
snd_hda_intel          32765  4 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
ir_mce_kbd_decoder     12681  0 
tda8290                22216  0 
ir_sony_decoder        12462  0 
ir_jvc_decoder         12459  0 
tea5767                13113  0 
ir_rc6_decoder         12459  0 
tuner                  26836  2 
ir_rc5_decoder         12459  0 
snd_ctxfi              86200  2 
ir_nec_decoder         12459  0 
snd_pcm                80845  4 snd_hda_intel,snd_hda_codec,snd_ctxfi
cx8800                 33328  0 
cx88xx                 83089  1 cx8800
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
tveeprom               17009  1 cx88xx
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
sp5100_tco             13495  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
videobuf_dma_sg        18786  2 cx8800,cx88xx
snd                    62064  21 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                  12849  0 
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              14635  1 snd
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
i2c_piix4              13093  0 
k10temp                12990  0 
serio_raw              13027  0 
dm_multipath           22710  0 
mac_hid                13077  0 
parport_pc             32114  1 
asus_atk0110           17742  0 
wmi                    18744  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  66 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
pata_atiixp            12999  4 
r8169                  56321  0 
sata_sil24             17794  1 
ati_agp                13242  0 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    3958216     165960          0     669252    1715840
-/+ buffers/cache:    1573124    2551052
Swap:     11829568        828   11828740

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable hibernate hibernate:
umount: /dev/zram0: not mounted

/etc/pm/sleep.d/95_zram_disable hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Thu Nov  1 22:16:48 CET 2012: performing hibernate
Initial commandline parameters: 
Fri Nov  2 16:40:43 CET 2012: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
decnet                 66360  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22528  0 
tda9887                17874  1 
tda8290                22216  0 
tea5767                13113  0 
tuner                  26836  2 
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
ir_mce_kbd_decoder     12681  0 
ir_sony_decoder        12462  0 
cx8800                 33328  0 
ir_jvc_decoder         12459  0 
ir_rc6_decoder         12459  0 
ir_rc5_decoder         12459  0 
ir_nec_decoder         12459  0 
cx88xx                 83089  1 cx8800
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
sp5100_tco             13495  0 
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
serio_raw              13027  0 
mac_hid                13077  0 
dm_multipath           22710  0 
btcx_risc              13400  2 cx8800,cx88xx
i2c_piix4              13093  0 
ppdev                  12849  0 
snd_hda_codec_via      46138  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
snd_ctxfi              86200  2 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  20 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_ctxfi,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
k10temp                12990  0 
parport_pc             32114  1 
asus_atk0110           17742  0 
wmi                    18744  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  50 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
pata_atiixp            12999  4 
r8169                  56321  0 
sata_sil24             17794  1 
ati_agp                13242  0 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    2092036    2032140          0     140948    1158180
-/+ buffers/cache:     792908    3331268
Swap:     11829568          0   11829568

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable hibernate hibernate:
umount: /dev/zram0: not mounted

/etc/pm/sleep.d/95_zram_disable hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Fri Nov  2 16:40:45 CET 2012: performing hibernate
Initial commandline parameters: 
Sat Nov  3 02:26:37 CET 2012: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
uvcvideo               67203  0 
snd_usb_audio         101566  0 
snd_usbmidi_lib        24603  1 snd_usb_audio
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
decnet                 66360  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22528  5 
snd_hda_codec_via      46138  1 
snd_hda_intel          32765  4 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
snd_ctxfi              86200  2 
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
snd_hwdep              13276  2 snd_usb_audio,snd_hda_codec
ir_mce_kbd_decoder     12681  0 
snd_pcm                80845  5 snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_ctxfi
tda9887                17874  1 
ir_sony_decoder        12462  0 
snd_seq_midi           13132  0 
ir_jvc_decoder         12459  0 
tda8290                22216  0 
snd_rawmidi            25424  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ir_rc6_decoder         12459  0 
ir_rc5_decoder         12459  0 
tea5767                13113  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ir_nec_decoder         12459  0 
tuner                  26836  2 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cx8800                 33328  0 
cx88xx                 83089  1 cx8800
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
snd                    62064  23 snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_ctxfi,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tveeprom               17009  1 cx88xx
sp5100_tco             13495  0 
soundcore              14635  1 snd
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               86588  5 uvcvideo,tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
ppdev                  12849  0 
i2c_piix4              13093  0 
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
k10temp                12990  0 
dm_multipath           22710  0 
serio_raw              13027  0 
asus_atk0110           17742  0 
parport_pc             32114  1 
mac_hid                13077  0 
wmi                    18744  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  50 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
r8169                  56321  0 
pata_atiixp            12999  4 
ati_agp                13242  0 
sata_sil24             17794  1 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    3992216     131960          0     667844    1818676
-/+ buffers/cache:    1505696    2618480
Swap:     11829568       8260   11821308

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable hibernate hibernate:
umount: /dev/zram0: not mounted

/etc/pm/sleep.d/95_zram_disable hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Sat Nov  3 02:26:41 CET 2012: performing hibernate
Initial commandline parameters: 
Sat Nov  3 13:31:21 CET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
ufs                    78131  0 
qnx4                   13309  0 
hfsplus                83507  0 
hfs                    49479  0 
minix                  31418  0 
ntfs                  100171  0 
vfat                   17308  0 
msdos                  17132  0 
fat                    55605  2 vfat,msdos
jfs                   175085  0 
xfs                   747494  0 
reiserfs              230896  0 
ext2                   67987  0 
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
decnet                 66360  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22528  5 
snd_hda_codec_via      46138  1 
snd_hda_intel          32765  4 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
tda9887                17874  1 
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
snd_ctxfi              86200  2 
snd_pcm                80845  4 snd_hda_intel,snd_hda_codec,snd_ctxfi
tda8290                22216  0 
ir_mce_kbd_decoder     12681  0 
snd_seq_midi           13132  0 
ir_sony_decoder        12462  0 
snd_rawmidi            25424  1 snd_seq_midi
tea5767                13113  0 
ir_jvc_decoder         12459  0 
snd_seq_midi_event     14475  1 snd_seq_midi
tuner                  26836  2 
ir_rc6_decoder         12459  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ir_rc5_decoder         12459  0 
snd_timer              28931  2 snd_pcm,snd_seq
ir_nec_decoder         12459  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cx8800                 33328  0 
cx88xx                 83089  1 cx8800
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
sp5100_tco             13495  0 
snd                    62064  21 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tveeprom               17009  1 cx88xx
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              14635  1 snd
dm_multipath           22710  0 
ppdev                  12849  0 
i2c_piix4              13093  0 
btcx_risc              13400  2 cx8800,cx88xx
k10temp                12990  0 
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
serio_raw              13027  0 
asus_atk0110           17742  0 
parport_pc             32114  1 
mac_hid                13077  0 
wmi                    18744  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  66 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
r8169                  56321  0 
sata_sil24             17794  1 
pata_atiixp            12999  4 
ati_agp                13242  0 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    3098352    1025824          0     596884    1412116
-/+ buffers/cache:    1089352    3034824
Swap:     11829568          0   11829568

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable suspend suspend:

/etc/pm/sleep.d/95_zram_disable suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sat Nov  3 13:31:23 CET 2012: performing suspend
Sat Nov  3 16:21:07 CET 2012: Awake.
Sat Nov  3 16:21:07 CET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable resume suspend:

/etc/pm/sleep.d/95_zram_disable resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Sat Nov  3 16:21:08 CET 2012: Finished.
Initial commandline parameters: 
Sun Nov  4 03:55:50 CET 2012: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
decnet                 66360  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22528  5 
tda9887                17874  1 
tda8290                22216  0 
tea5767                13113  0 
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
ir_mce_kbd_decoder     12681  0 
ir_sony_decoder        12462  0 
snd_hda_codec_via      46138  1 
tuner                  26836  2 
ir_jvc_decoder         12459  0 
ir_rc6_decoder         12459  0 
snd_hda_intel          32765  4 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
ir_rc5_decoder         12459  0 
snd_ctxfi              86200  2 
snd_pcm                80845  4 snd_hda_intel,snd_hda_codec,snd_ctxfi
ir_nec_decoder         12459  0 
snd_seq_midi           13132  0 
cx8800                 33328  0 
cx88xx                 83089  1 cx8800
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  21 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              14635  1 snd
ppdev                  12849  0 
sp5100_tco             13495  0 
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
btcx_risc              13400  2 cx8800,cx88xx
k10temp                12990  0 
i2c_piix4              13093  0 
dm_multipath           22710  0 
serio_raw              13027  0 
asus_atk0110           17742  0 
parport_pc             32114  1 
mac_hid                13077  0 
wmi                    18744  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  50 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
pata_atiixp            12999  4 
sata_sil24             17794  1 
r8169                  56321  0 
ati_agp                13242  0 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    3891872     232304          0     639316    1570308
-/+ buffers/cache:    1682248    2441928
Swap:     11829568        284   11829284

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable hibernate hibernate:
umount: /dev/zram0: not mounted

/etc/pm/sleep.d/95_zram_disable hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Sun Nov  4 03:55:54 CET 2012: performing hibernate
Initial commandline parameters: 
Sun Nov  4 19:23:53 CET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
decnet                 66360  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22528  5 
tda9887                17874  1 
tda8290                22216  0 
tea5767                13113  0 
tuner                  26836  2 
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
ir_mce_kbd_decoder     12681  0 
ir_sony_decoder        12462  0 
snd_hda_codec_via      46138  1 
cx8800                 33328  0 
snd_hda_intel          32765  4 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
ir_jvc_decoder         12459  0 
snd_ctxfi              86200  2 
snd_pcm                80845  4 snd_hda_intel,snd_hda_codec,snd_ctxfi
ir_rc6_decoder         12459  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ir_rc5_decoder         12459  0 
cx88xx                 83089  1 cx8800
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ir_nec_decoder         12459  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  21 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,cx88xx,ir_nec_decoder
i2c_algo_bit           13199  1 cx88xx
ppdev                  12849  0 
tveeprom               17009  1 cx88xx
soundcore              14635  1 snd
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
sp5100_tco             13495  0 
i2c_piix4              13093  0 
mac_hid                13077  0 
btcx_risc              13400  2 cx8800,cx88xx
serio_raw              13027  0 
dm_multipath           22710  0 
parport_pc             32114  1 
asus_atk0110           17742  0 
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
k10temp                12990  0 
wmi                    18744  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  50 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
pata_atiixp            12999  4 
r8169                  56321  0 
sata_sil24             17794  1 
ati_agp                13242  0 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    3364820     759356          0     673972    1285692
-/+ buffers/cache:    1405156    2719020
Swap:     11829568        252   11829316

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable suspend suspend:

/etc/pm/sleep.d/95_zram_disable suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sun Nov  4 19:23:56 CET 2012: performing suspend
Sun Nov  4 19:44:15 CET 2012: Awake.
Sun Nov  4 19:44:15 CET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable resume suspend:

/etc/pm/sleep.d/95_zram_disable resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Sun Nov  4 19:44:16 CET 2012: Finished.
Initial commandline parameters: 
Sun Nov  4 23:42:19 CET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
decnet                 66360  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22528  5 
tda9887                17874  1 
tda8290                22216  0 
tea5767                13113  0 
tuner                  26836  2 
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
ir_mce_kbd_decoder     12681  0 
ir_sony_decoder        12462  0 
snd_hda_codec_via      46138  1 
cx8800                 33328  0 
snd_hda_intel          32765  4 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
ir_jvc_decoder         12459  0 
snd_ctxfi              86200  2 
snd_pcm                80845  4 snd_hda_intel,snd_hda_codec,snd_ctxfi
ir_rc6_decoder         12459  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ir_rc5_decoder         12459  0 
cx88xx                 83089  1 cx8800
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ir_nec_decoder         12459  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  21 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,cx88xx,ir_nec_decoder
i2c_algo_bit           13199  1 cx88xx
ppdev                  12849  0 
tveeprom               17009  1 cx88xx
soundcore              14635  1 snd
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
sp5100_tco             13495  0 
i2c_piix4              13093  0 
mac_hid                13077  0 
btcx_risc              13400  2 cx8800,cx88xx
serio_raw              13027  0 
dm_multipath           22710  0 
parport_pc             32114  1 
asus_atk0110           17742  0 
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
k10temp                12990  0 
wmi                    18744  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  58 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
pata_atiixp            12999  4 
r8169                  56321  0 
sata_sil24             17794  1 
ati_agp                13242  0 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    3973032     151144          0     668824    1984156
-/+ buffers/cache:    1320052    2804124
Swap:     11829568        244   11829324

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable suspend suspend:

/etc/pm/sleep.d/95_zram_disable suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sun Nov  4 23:42:22 CET 2012: performing suspend
Mon Nov  5 09:27:48 CET 2012: Awake.
Mon Nov  5 09:27:48 CET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable resume suspend:

/etc/pm/sleep.d/95_zram_disable resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Mon Nov  5 09:27:49 CET 2012: Finished.
Initial commandline parameters: 
Tue Nov  6 00:27:48 CET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
decnet                 66360  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22528  5 
tda9887                17874  1 
tda8290                22216  0 
tea5767                13113  0 
tuner                  26836  2 
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
snd_hda_codec_via      46138  1 
cx8800                 33328  0 
snd_hda_intel          32765  4 
ir_mce_kbd_decoder     12681  0 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
snd_ctxfi              86200  2 
snd_hwdep              13276  1 snd_hda_codec
ir_sony_decoder        12462  0 
snd_pcm                80845  4 snd_hda_intel,snd_hda_codec,snd_ctxfi
ir_jvc_decoder         12459  0 
snd_seq_midi           13132  0 
ir_rc6_decoder         12459  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ir_rc5_decoder         12459  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
cx88xx                 83089  1 cx8800
ir_nec_decoder         12459  0 
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
videobuf_dma_sg        18786  2 cx8800,cx88xx
snd                    62064  21 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_ctxfi,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              14635  1 snd
ppdev                  12849  0 
sp5100_tco             13495  0 
i2c_piix4              13093  0 
btcx_risc              13400  2 cx8800,cx88xx
k10temp                12990  0 
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
dm_multipath           22710  0 
serio_raw              13027  0 
asus_atk0110           17742  0 
parport_pc             32114  1 
mac_hid                13077  0 
wmi                    18744  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  50 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
pata_atiixp            12999  4 
sata_sil24             17794  1 
r8169                  56321  0 
ati_agp                13242  0 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    3974020     150156          0     674008    2211580
-/+ buffers/cache:    1088432    3035744
Swap:     11829568          0   11829568

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable suspend suspend:

/etc/pm/sleep.d/95_zram_disable suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Tue Nov  6 00:27:51 CET 2012: performing suspend
Tue Nov  6 07:28:51 CET 2012: Awake.
Tue Nov  6 07:28:51 CET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable resume suspend:

/etc/pm/sleep.d/95_zram_disable resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Tue Nov  6 07:28:52 CET 2012: Finished.
Initial commandline parameters: 
Tue Nov  6 09:03:21 CET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
decnet                 66360  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22528  5 
tda9887                17874  1 
tda8290                22216  0 
tea5767                13113  0 
tuner                  26836  2 
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
snd_hda_codec_via      46138  1 
cx8800                 33328  0 
snd_hda_intel          32765  3 
ir_mce_kbd_decoder     12681  0 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
snd_ctxfi              86200  2 
snd_hwdep              13276  1 snd_hda_codec
ir_sony_decoder        12462  0 
snd_pcm                80845  3 snd_hda_intel,snd_hda_codec,snd_ctxfi
ir_jvc_decoder         12459  0 
snd_seq_midi           13132  0 
ir_rc6_decoder         12459  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ir_rc5_decoder         12459  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
cx88xx                 83089  1 cx8800
ir_nec_decoder         12459  0 
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
videobuf_dma_sg        18786  2 cx8800,cx88xx
snd                    62064  20 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_ctxfi,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              14635  1 snd
ppdev                  12849  0 
sp5100_tco             13495  0 
i2c_piix4              13093  0 
btcx_risc              13400  2 cx8800,cx88xx
k10temp                12990  0 
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
dm_multipath           22710  0 
serio_raw              13027  0 
asus_atk0110           17742  0 
parport_pc             32114  1 
mac_hid                13077  0 
wmi                    18744  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  58 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
pata_atiixp            12999  4 
sata_sil24             17794  1 
r8169                  56321  0 
ati_agp                13242  0 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    3747560     376616          0     585136    2001144
-/+ buffers/cache:    1161280    2962896
Swap:     11829568          4   11829564

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable suspend suspend:

/etc/pm/sleep.d/95_zram_disable suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Tue Nov  6 09:03:23 CET 2012: performing suspend
Tue Nov  6 10:38:11 CET 2012: Awake.
Tue Nov  6 10:38:11 CET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable resume suspend:

/etc/pm/sleep.d/95_zram_disable resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Tue Nov  6 10:38:12 CET 2012: Finished.
Initial commandline parameters: 
Wed Nov  7 00:14:09 CET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
decnet                 66360  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22528  5 
snd_hda_codec_via      46138  1 
snd_hda_intel          32765  4 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_ctxfi              86200  2 
snd_pcm                80845  4 snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_seq_midi           13132  0 
tda9887                17874  1 
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
ir_mce_kbd_decoder     12681  0 
tda8290                22216  0 
ir_sony_decoder        12462  0 
ir_jvc_decoder         12459  0 
tea5767                13113  0 
ir_rc6_decoder         12459  0 
tuner                  26836  2 
ir_rc5_decoder         12459  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ir_nec_decoder         12459  0 
cx8800                 33328  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cx88xx                 83089  1 cx8800
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
snd                    62064  21 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tveeprom               17009  1 cx88xx
ppdev                  12849  0 
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              14635  1 snd
sp5100_tco             13495  0 
i2c_piix4              13093  0 
btcx_risc              13400  2 cx8800,cx88xx
k10temp                12990  0 
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
dm_multipath           22710  0 
serio_raw              13027  0 
asus_atk0110           17742  0 
parport_pc             32114  1 
mac_hid                13077  0 
wmi                    18744  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  50 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
pata_atiixp            12999  4 
sata_sil24             17794  1 
ati_agp                13242  0 
r8169                  56321  0 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    3770244     353932          0     679708    1954308
-/+ buffers/cache:    1136228    2987948
Swap:     11829568          0   11829568

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable suspend suspend:

/etc/pm/sleep.d/95_zram_disable suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Wed Nov  7 00:14:12 CET 2012: performing suspend
Wed Nov  7 09:28:37 CET 2012: Awake.
Wed Nov  7 09:28:37 CET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable resume suspend:

/etc/pm/sleep.d/95_zram_disable resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Wed Nov  7 09:28:38 CET 2012: Finished.
Initial commandline parameters: 
Thu Nov  8 00:47:37 CET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
decnet                 66360  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22528  5 
tda9887                17874  1 
tda8290                22216  0 
ir_lirc_codec          12739  0 
tea5767                13113  0 
lirc_dev               18700  1 ir_lirc_codec
ir_mce_kbd_decoder     12681  0 
ir_sony_decoder        12462  0 
tuner                  26836  2 
ir_jvc_decoder         12459  0 
ir_rc6_decoder         12459  0 
ir_rc5_decoder         12459  0 
ir_nec_decoder         12459  0 
cx8800                 33328  0 
cx88xx                 83089  1 cx8800
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
snd_hda_codec_via      46138  1 
snd_hda_intel          32765  4 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_ctxfi              86200  2 
snd_seq_midi           13132  0 
snd_pcm                80845  4 snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  21 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              14635  1 snd
ppdev                  12849  0 
sp5100_tco             13495  0 
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
btcx_risc              13400  2 cx8800,cx88xx
k10temp                12990  0 
i2c_piix4              13093  0 
serio_raw              13027  0 
dm_multipath           22710  0 
asus_atk0110           17742  0 
parport_pc             32114  1 
mac_hid                13077  0 
wmi                    18744  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  50 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
pata_atiixp            12999  4 
r8169                  56321  0 
sata_sil24             17794  1 
ati_agp                13242  0 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    3959528     164648          0     655956    1986880
-/+ buffers/cache:    1316692    2807484
Swap:     11829568          0   11829568

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable suspend suspend:

/etc/pm/sleep.d/95_zram_disable suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Nov  8 00:47:40 CET 2012: performing suspend
Thu Nov  8 09:28:37 CET 2012: Awake.
Thu Nov  8 09:28:37 CET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable resume suspend:

/etc/pm/sleep.d/95_zram_disable resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Thu Nov  8 09:28:38 CET 2012: Finished.
Initial commandline parameters: 
Fri Nov  9 00:52:43 CET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
decnet                 66360  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22528  5 
tda9887                17874  1 
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
tda8290                22216  0 
ir_mce_kbd_decoder     12681  0 
ir_sony_decoder        12462  0 
ir_jvc_decoder         12459  0 
tea5767                13113  0 
ir_rc6_decoder         12459  0 
tuner                  26836  2 
snd_hda_codec_via      46138  1 
ir_rc5_decoder         12459  0 
ir_nec_decoder         12459  0 
cx8800                 33328  0 
cx88xx                 83089  1 cx8800
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
snd_hda_intel          32765  4 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_ctxfi              86200  2 
snd_seq_midi           13132  0 
snd_pcm                80845  4 snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
v4l2_common            15793  3 tuner,cx8800,cx88xx
snd                    62064  21 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
soundcore              14635  1 snd
sp5100_tco             13495  0 
ppdev                  12849  0 
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
btcx_risc              13400  2 cx8800,cx88xx
i2c_piix4              13093  0 
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
k10temp                12990  0 
dm_multipath           22710  0 
serio_raw              13027  0 
asus_atk0110           17742  0 
parport_pc             32114  1 
mac_hid                13077  0 
wmi                    18744  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  50 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
pata_atiixp            12999  4 
sata_sil24             17794  1 
r8169                  56321  0 
ati_agp                13242  0 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    3953496     170680          0     667104    2182508
-/+ buffers/cache:    1103884    3020292
Swap:     11829568          0   11829568

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable suspend suspend:

/etc/pm/sleep.d/95_zram_disable suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Nov  9 00:52:46 CET 2012: performing suspend
Fri Nov  9 08:30:36 CET 2012: Awake.
Fri Nov  9 08:30:36 CET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable resume suspend:

/etc/pm/sleep.d/95_zram_disable resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Fri Nov  9 08:30:37 CET 2012: Finished.
Initial commandline parameters: 
Fri Nov  9 09:27:26 CET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
decnet                 66360  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22528  5 
tda9887                17874  1 
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
tda8290                22216  0 
ir_mce_kbd_decoder     12681  0 
ir_sony_decoder        12462  0 
ir_jvc_decoder         12459  0 
tea5767                13113  0 
ir_rc6_decoder         12459  0 
tuner                  26836  2 
snd_hda_codec_via      46138  1 
ir_rc5_decoder         12459  0 
ir_nec_decoder         12459  0 
cx8800                 33328  0 
cx88xx                 83089  1 cx8800
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_ctxfi              86200  2 
snd_seq_midi           13132  0 
snd_pcm                80845  3 snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
v4l2_common            15793  3 tuner,cx8800,cx88xx
snd                    62064  20 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
soundcore              14635  1 snd
sp5100_tco             13495  0 
ppdev                  12849  0 
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
btcx_risc              13400  2 cx8800,cx88xx
i2c_piix4              13093  0 
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
k10temp                12990  0 
dm_multipath           22710  0 
serio_raw              13027  0 
asus_atk0110           17742  0 
parport_pc             32114  1 
mac_hid                13077  0 
wmi                    18744  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  58 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
pata_atiixp            12999  4 
sata_sil24             17794  1 
r8169                  56321  0 
ati_agp                13242  0 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    3898216     225960          0     613408    2047512
-/+ buffers/cache:    1237296    2886880
Swap:     11829568          0   11829568

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable suspend suspend:

/etc/pm/sleep.d/95_zram_disable suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Nov  9 09:27:29 CET 2012: performing suspend
Fri Nov  9 11:48:18 CET 2012: Awake.
Fri Nov  9 11:48:18 CET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable resume suspend:

/etc/pm/sleep.d/95_zram_disable resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Fri Nov  9 11:48:19 CET 2012: Finished.
Initial commandline parameters: 
Fri Nov  9 15:15:41 CET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
decnet                 66360  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22528  5 
tda9887                17874  1 
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
tda8290                22216  0 
ir_mce_kbd_decoder     12681  0 
ir_sony_decoder        12462  0 
ir_jvc_decoder         12459  0 
tea5767                13113  0 
ir_rc6_decoder         12459  0 
tuner                  26836  2 
snd_hda_codec_via      46138  1 
ir_rc5_decoder         12459  0 
ir_nec_decoder         12459  0 
cx8800                 33328  0 
cx88xx                 83089  1 cx8800
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_ctxfi              86200  2 
snd_seq_midi           13132  0 
snd_pcm                80845  3 snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
v4l2_common            15793  3 tuner,cx8800,cx88xx
snd                    62064  20 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
soundcore              14635  1 snd
sp5100_tco             13495  0 
ppdev                  12849  0 
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
btcx_risc              13400  2 cx8800,cx88xx
i2c_piix4              13093  0 
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
k10temp                12990  0 
dm_multipath           22710  0 
serio_raw              13027  0 
asus_atk0110           17742  0 
parport_pc             32114  1 
mac_hid                13077  0 
wmi                    18744  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  58 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
pata_atiixp            12999  4 
sata_sil24             17794  1 
r8169                  56321  0 
ati_agp                13242  0 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    2287528    1836648          0     280152     604904
-/+ buffers/cache:    1402472    2721704
Swap:     11829568      15492   11814076

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable suspend suspend:

/etc/pm/sleep.d/95_zram_disable suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Nov  9 15:15:53 CET 2012: performing suspend
Fri Nov  9 19:28:58 CET 2012: Awake.
Fri Nov  9 19:28:58 CET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable resume suspend:

/etc/pm/sleep.d/95_zram_disable resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Fri Nov  9 19:28:58 CET 2012: Finished.
Initial commandline parameters: 
Fri Nov  9 20:48:21 CET 2012: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
decnet                 66360  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22528  5 
snd_hda_codec_via      46138  1 
tda9887                17874  1 
tda8290                22216  0 
tea5767                13113  0 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
tuner                  26836  2 
snd_ctxfi              86200  2 
snd_pcm                80845  3 snd_hda_intel,snd_hda_codec,snd_ctxfi
ir_mce_kbd_decoder     12681  0 
cx8800                 33328  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
ir_sony_decoder        12462  0 
ir_jvc_decoder         12459  0 
snd_seq_midi_event     14475  1 snd_seq_midi
ir_rc6_decoder         12459  0 
cx88xx                 83089  1 cx8800
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ir_rc5_decoder         12459  0 
ir_nec_decoder         12459  0 
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,cx88xx,ir_rc5_decoder,ir_nec_decoder
snd                    62064  20 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
v4l2_common            15793  3 tuner,cx8800,cx88xx
soundcore              14635  1 snd
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
ppdev                  12849  0 
sp5100_tco             13495  0 
i2c_piix4              13093  0 
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
dm_multipath           22710  0 
k10temp                12990  0 
serio_raw              13027  0 
parport_pc             32114  1 
mac_hid                13077  0 
asus_atk0110           17742  0 
wmi                    18744  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  50 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
pata_atiixp            12999  4 
r8169                  56321  0 
sata_sil24             17794  1 
ati_agp                13242  0 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    3621100     503076          0     663544    1908704
-/+ buffers/cache:    1048852    3075324
Swap:     11829568          0   11829568

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable hibernate hibernate:
umount: /dev/zram0: not mounted

/etc/pm/sleep.d/95_zram_disable hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Fri Nov  9 20:48:25 CET 2012: performing hibernate
Initial commandline parameters: 
sob, 10 lis 2012, 02:23:39 CET: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
decnet                 66360  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22528  0 
tda9887                17874  1 
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
tda8290                22216  0 
ir_mce_kbd_decoder     12681  0 
tea5767                13113  0 
ir_sony_decoder        12462  0 
ir_jvc_decoder         12459  0 
tuner                  26836  2 
ir_rc6_decoder         12459  0 
ir_rc5_decoder         12459  0 
snd_hda_codec_via      46138  1 
ir_nec_decoder         12459  0 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
cx8800                 33328  0 
cx88xx                 83089  1 cx8800
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
snd_ctxfi              86200  2 
tveeprom               17009  1 cx88xx
snd_seq_midi           13132  0 
snd_pcm                80845  3 snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  20 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
dm_multipath           22710  0 
ppdev                  12849  0 
soundcore              14635  1 snd
sp5100_tco             13495  0 
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
serio_raw              13027  0 
btcx_risc              13400  2 cx8800,cx88xx
i2c_piix4              13093  0 
k10temp                12990  0 
mac_hid                13077  0 
parport_pc             32114  1 
asus_atk0110           17742  0 
wmi                    18744  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  50 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
pata_atiixp            12999  4 
sata_sil24             17794  1 
ati_agp                13242  0 
r8169                  56321  0 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    2796320    1327856          0     572804    1016552
-/+ buffers/cache:    1206964    2917212
Swap:     11829568          0   11829568

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable hibernate hibernate:
umount: /dev/zram0: nie jest zamontowane

/etc/pm/sleep.d/95_zram_disable hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
sob, 10 lis 2012, 02:23:42 CET: performing hibernate
Initial commandline parameters: 
Sat Nov 10 04:07:15 CET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
decnet                 66360  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22528  5 
tda9887                17874  1 
tda8290                22216  0 
tea5767                13113  0 
tuner                  26836  2 
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
cx8800                 33328  0 
cx88xx                 83089  1 cx8800
snd_hda_codec_via      46138  1 
snd_hda_intel          32765  4 
ir_mce_kbd_decoder     12681  0 
snd_ctxfi              86200  2 
ir_sony_decoder        12462  0 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
ir_jvc_decoder         12459  0 
snd_pcm                80845  4 snd_hda_intel,snd_ctxfi,snd_hda_codec
ir_rc6_decoder         12459  0 
snd_seq_midi           13132  0 
ir_rc5_decoder         12459  0 
ir_nec_decoder         12459  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
rc_core                21263  8 ir_lirc_codec,cx88xx,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder
i2c_algo_bit           13199  1 cx88xx
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
tveeprom               17009  1 cx88xx
ppdev                  12849  0 
sp5100_tco             13495  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
v4l2_common            15793  3 tuner,cx8800,cx88xx
snd                    62064  21 snd_hda_codec_via,snd_hda_intel,snd_ctxfi,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
i2c_piix4              13093  0 
soundcore              14635  1 snd
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
k10temp                12990  0 
dm_multipath           22710  0 
serio_raw              13027  0 
asus_atk0110           17742  0 
parport_pc             32114  1 
mac_hid                13077  0 
wmi                    18744  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  50 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
pata_atiixp            12999  4 
sata_sil24             17794  1 
r8169                  56321  0 
ati_agp                13242  0 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    3665852     458324          0     655116    1699488
-/+ buffers/cache:    1311248    2812928
Swap:     11829568        204   11829364

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable suspend suspend:

/etc/pm/sleep.d/95_zram_disable suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sat Nov 10 04:07:18 CET 2012: performing suspend
Sat Nov 10 10:38:06 CET 2012: Awake.
Sat Nov 10 10:38:06 CET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable resume suspend:

/etc/pm/sleep.d/95_zram_disable resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Sat Nov 10 10:38:07 CET 2012: Finished.
Initial commandline parameters: 
Sun Nov 11 02:32:30 CET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
decnet                 66360  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22528  5 
tda9887                17874  1 
tda8290                22216  0 
tea5767                13113  0 
tuner                  26836  2 
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
cx8800                 33328  0 
cx88xx                 83089  1 cx8800
snd_hda_codec_via      46138  1 
snd_hda_intel          32765  4 
ir_mce_kbd_decoder     12681  0 
snd_ctxfi              86200  2 
ir_sony_decoder        12462  0 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
ir_jvc_decoder         12459  0 
snd_pcm                80845  4 snd_hda_intel,snd_ctxfi,snd_hda_codec
ir_rc6_decoder         12459  0 
snd_seq_midi           13132  0 
ir_rc5_decoder         12459  0 
ir_nec_decoder         12459  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
rc_core                21263  8 ir_lirc_codec,cx88xx,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder
i2c_algo_bit           13199  1 cx88xx
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
tveeprom               17009  1 cx88xx
ppdev                  12849  0 
sp5100_tco             13495  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
v4l2_common            15793  3 tuner,cx8800,cx88xx
snd                    62064  21 snd_hda_codec_via,snd_hda_intel,snd_ctxfi,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
i2c_piix4              13093  0 
soundcore              14635  1 snd
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
k10temp                12990  0 
dm_multipath           22710  0 
serio_raw              13027  0 
asus_atk0110           17742  0 
parport_pc             32114  1 
mac_hid                13077  0 
wmi                    18744  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  74 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
pata_atiixp            12999  4 
sata_sil24             17794  1 
r8169                  56321  0 
ati_agp                13242  0 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    3429680     694496          0     638564     624092
-/+ buffers/cache:    2167024    1957152
Swap:     11829568      68980   11760588

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable suspend suspend:

/etc/pm/sleep.d/95_zram_disable suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sun Nov 11 02:32:34 CET 2012: performing suspend
Sun Nov 11 13:27:21 CET 2012: Awake.
Sun Nov 11 13:27:21 CET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable resume suspend:

/etc/pm/sleep.d/95_zram_disable resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Sun Nov 11 13:27:22 CET 2012: Finished.
Initial commandline parameters: 
Sun Nov 11 14:11:24 CET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
decnet                 66360  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22528  5 
tda9887                17874  1 
tda8290                22216  0 
tea5767                13113  0 
tuner                  26836  2 
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
cx8800                 33328  0 
cx88xx                 83089  1 cx8800
snd_hda_codec_via      46138  1 
snd_hda_intel          32765  3 
ir_mce_kbd_decoder     12681  0 
snd_ctxfi              86200  2 
ir_sony_decoder        12462  0 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
ir_jvc_decoder         12459  0 
snd_pcm                80845  3 snd_hda_intel,snd_ctxfi,snd_hda_codec
ir_rc6_decoder         12459  0 
snd_seq_midi           13132  0 
ir_rc5_decoder         12459  0 
ir_nec_decoder         12459  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
rc_core                21263  8 ir_lirc_codec,cx88xx,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder
i2c_algo_bit           13199  1 cx88xx
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
tveeprom               17009  1 cx88xx
ppdev                  12849  0 
sp5100_tco             13495  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
v4l2_common            15793  3 tuner,cx8800,cx88xx
snd                    62064  20 snd_hda_codec_via,snd_hda_intel,snd_ctxfi,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
i2c_piix4              13093  0 
soundcore              14635  1 snd
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
k10temp                12990  0 
dm_multipath           22710  0 
serio_raw              13027  0 
asus_atk0110           17742  0 
parport_pc             32114  1 
mac_hid                13077  0 
wmi                    18744  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  58 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
pata_atiixp            12999  4 
sata_sil24             17794  1 
r8169                  56321  0 
ati_agp                13242  0 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    3326996     797180          0     417328     579116
-/+ buffers/cache:    2330552    1793624
Swap:     11829568      69216   11760352

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable suspend suspend:

/etc/pm/sleep.d/95_zram_disable suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sun Nov 11 14:11:27 CET 2012: performing suspend
Sun Nov 11 14:23:18 CET 2012: Awake.
Sun Nov 11 14:23:18 CET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable resume suspend:

/etc/pm/sleep.d/95_zram_disable resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Sun Nov 11 14:23:18 CET 2012: Finished.
Initial commandline parameters: 
Sun Nov 11 14:32:16 CET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
decnet                 66360  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22528  5 
tda9887                17874  1 
tda8290                22216  0 
tea5767                13113  0 
tuner                  26836  2 
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
cx8800                 33328  0 
cx88xx                 83089  1 cx8800
snd_hda_codec_via      46138  1 
snd_hda_intel          32765  3 
ir_mce_kbd_decoder     12681  0 
snd_ctxfi              86200  2 
ir_sony_decoder        12462  0 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
ir_jvc_decoder         12459  0 
snd_pcm                80845  3 snd_hda_intel,snd_ctxfi,snd_hda_codec
ir_rc6_decoder         12459  0 
snd_seq_midi           13132  0 
ir_rc5_decoder         12459  0 
ir_nec_decoder         12459  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
rc_core                21263  8 ir_lirc_codec,cx88xx,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder
i2c_algo_bit           13199  1 cx88xx
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
tveeprom               17009  1 cx88xx
ppdev                  12849  0 
sp5100_tco             13495  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
v4l2_common            15793  3 tuner,cx8800,cx88xx
snd                    62064  20 snd_hda_codec_via,snd_hda_intel,snd_ctxfi,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
i2c_piix4              13093  0 
soundcore              14635  1 snd
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
k10temp                12990  0 
dm_multipath           22710  0 
serio_raw              13027  0 
asus_atk0110           17742  0 
parport_pc             32114  1 
mac_hid                13077  0 
wmi                    18744  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  58 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
pata_atiixp            12999  4 
sata_sil24             17794  1 
r8169                  56321  0 
ati_agp                13242  0 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    3355568     768608          0     424400     605696
-/+ buffers/cache:    2325472    1798704
Swap:     11829568      69196   11760372

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable suspend suspend:

/etc/pm/sleep.d/95_zram_disable suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sun Nov 11 14:32:18 CET 2012: performing suspend
Sun Nov 11 19:51:24 CET 2012: Awake.
Sun Nov 11 19:51:24 CET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable resume suspend:

/etc/pm/sleep.d/95_zram_disable resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Sun Nov 11 19:51:24 CET 2012: Finished.
Initial commandline parameters: 
Sun Nov 11 22:49:44 CET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
decnet                 66360  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22528  5 
tda9887                17874  1 
tda8290                22216  0 
tea5767                13113  0 
tuner                  26836  2 
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
cx8800                 33328  0 
cx88xx                 83089  1 cx8800
snd_hda_codec_via      46138  1 
snd_hda_intel          32765  4 
ir_mce_kbd_decoder     12681  0 
snd_ctxfi              86200  2 
ir_sony_decoder        12462  0 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
ir_jvc_decoder         12459  0 
snd_pcm                80845  4 snd_hda_intel,snd_ctxfi,snd_hda_codec
ir_rc6_decoder         12459  0 
snd_seq_midi           13132  0 
ir_rc5_decoder         12459  0 
ir_nec_decoder         12459  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
rc_core                21263  8 ir_lirc_codec,cx88xx,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder
i2c_algo_bit           13199  1 cx88xx
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
tveeprom               17009  1 cx88xx
ppdev                  12849  0 
sp5100_tco             13495  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
v4l2_common            15793  3 tuner,cx8800,cx88xx
snd                    62064  21 snd_hda_codec_via,snd_hda_intel,snd_ctxfi,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
i2c_piix4              13093  0 
soundcore              14635  1 snd
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
k10temp                12990  0 
dm_multipath           22710  0 
serio_raw              13027  0 
asus_atk0110           17742  0 
parport_pc             32114  1 
mac_hid                13077  0 
wmi                    18744  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  58 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
pata_atiixp            12999  4 
sata_sil24             17794  1 
r8169                  56321  0 
ati_agp                13242  0 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    3792944     331232          0     452060     966372
-/+ buffers/cache:    2374512    1749664
Swap:     11829568      74912   11754656

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable suspend suspend:

/etc/pm/sleep.d/95_zram_disable suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sun Nov 11 22:49:46 CET 2012: performing suspend
Mon Nov 12 04:27:43 CET 2012: Awake.
Mon Nov 12 04:27:43 CET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable resume suspend:

/etc/pm/sleep.d/95_zram_disable resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Mon Nov 12 04:27:44 CET 2012: Finished.
Initial commandline parameters: 
Mon Nov 12 22:48:37 CET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
ufs                    78131  0 
qnx4                   13309  0 
hfsplus                83507  0 
hfs                    49479  0 
minix                  31418  0 
ntfs                  100171  0 
vfat                   17308  0 
msdos                  17132  0 
fat                    55605  2 vfat,msdos
jfs                   175085  0 
xfs                   747494  0 
reiserfs              230896  0 
ext2                   67987  0 
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
decnet                 66360  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22528  5 
tda9887                17874  1 
tda8290                22216  0 
tea5767                13113  0 
tuner                  26836  2 
snd_hda_codec_via      46138  1 
snd_ctxfi              86200  2 
snd_hda_intel          32765  4 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
cx8800                 33328  0 
snd_hwdep              13276  1 snd_hda_codec
snd_seq_midi           13132  0 
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
ir_mce_kbd_decoder     12681  0 
snd_rawmidi            25424  1 snd_seq_midi
ir_sony_decoder        12462  0 
cx88xx                 83089  1 cx8800
snd_pcm                80845  4 snd_ctxfi,snd_hda_intel,snd_hda_codec
ir_jvc_decoder         12459  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ir_rc6_decoder         12459  0 
snd                    62064  21 snd_hda_codec_via,snd_ctxfi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
ir_rc5_decoder         12459  0 
ir_nec_decoder         12459  0 
ppdev                  12849  0 
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,cx88xx,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
sp5100_tco             13495  0 
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              14635  1 snd
serio_raw              13027  0 
btcx_risc              13400  2 cx8800,cx88xx
i2c_piix4              13093  0 
mac_hid                13077  0 
snd_page_alloc         14108  3 snd_ctxfi,snd_hda_intel,snd_pcm
k10temp                12990  0 
dm_multipath           22710  0 
parport_pc             32114  1 
asus_atk0110           17742  0 
wmi                    18744  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  50 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
pata_atiixp            12999  4 
sata_sil24             17794  1 
r8169                  56321  0 
ati_agp                13242  0 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    3931796     192380          0     641324    1924060
-/+ buffers/cache:    1366412    2757764
Swap:     11829568        248   11829320

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable suspend suspend:

/etc/pm/sleep.d/95_zram_disable suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Mon Nov 12 22:48:41 CET 2012: performing suspend
Tue Nov 13 04:28:33 CET 2012: Awake.
Tue Nov 13 04:28:33 CET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable resume suspend:

/etc/pm/sleep.d/95_zram_disable resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Tue Nov 13 04:28:34 CET 2012: Finished.
Initial commandline parameters: 
Tue Nov 13 22:43:36 CET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
decnet                 66360  0 [permanent]
dm_crypt               22528  5 
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
snd_hda_codec_via      46138  1 
snd_ctxfi              86200  2 
snd_hda_intel          32765  4 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
snd_hwdep              13276  1 snd_hda_codec
tda9887                17874  1 
snd_pcm                80845  4 snd_ctxfi,snd_hda_intel,snd_hda_codec
tda8290                22216  0 
ir_mce_kbd_decoder     12681  0 
snd_seq_midi           13132  0 
ir_sony_decoder        12462  0 
tea5767                13113  0 
ir_jvc_decoder         12459  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
tuner                  26836  2 
ir_rc6_decoder         12459  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ir_rc5_decoder         12459  0 
cx8800                 33328  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ir_nec_decoder         12459  0 
cx88xx                 83089  1 cx8800
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
v4l2_common            15793  3 tuner,cx8800,cx88xx
snd                    62064  21 snd_hda_codec_via,snd_ctxfi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
soundcore              14635  1 snd
videobuf_dma_sg        18786  2 cx8800,cx88xx
sp5100_tco             13495  0 
i2c_piix4              13093  0 
dm_multipath           22710  0 
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_ctxfi,snd_hda_intel,snd_pcm
ppdev                  12849  0 
k10temp                12990  0 
serio_raw              13027  0 
mac_hid                13077  0 
wmi                    18744  0 
parport_pc             32114  1 
asus_atk0110           17742  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  50 
binfmt_misc            17292  1 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
pata_atiixp            12999  4 
r8169                  56321  0 
ati_agp                13242  0 
sata_sil24             17794  1 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    3950096     174080          0     658968    2085220
-/+ buffers/cache:    1205908    2918268
Swap:     11829568        272   11829296

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable suspend suspend:

/etc/pm/sleep.d/95_zram_disable suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Tue Nov 13 22:43:39 CET 2012: performing suspend
Wed Nov 14 04:28:35 CET 2012: Awake.
Wed Nov 14 04:28:35 CET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable resume suspend:

/etc/pm/sleep.d/95_zram_disable resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Wed Nov 14 04:28:36 CET 2012: Finished.
Initial commandline parameters: 
Wed Nov 14 22:40:00 CET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
decnet                 66360  0 [permanent]
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
dm_crypt               22528  5 
tda9887                17874  1 
tda8290                22216  0 
tea5767                13113  0 
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
tuner                  26836  2 
ir_mce_kbd_decoder     12681  0 
ir_sony_decoder        12462  0 
ir_jvc_decoder         12459  0 
ir_rc6_decoder         12459  0 
snd_hda_codec_via      46138  1 
ir_rc5_decoder         12459  0 
snd_hda_intel          32765  4 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
ir_nec_decoder         12459  0 
cx8800                 33328  0 
cx88xx                 83089  1 cx8800
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
snd_ctxfi              86200  2 
snd_hwdep              13276  1 snd_hda_codec
snd_seq_midi           13132  0 
sp5100_tco             13495  0 
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
snd_pcm                80845  4 snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
serio_raw              13027  0 
videobuf_dma_sg        18786  2 cx8800,cx88xx
dm_multipath           22710  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  21 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_ctxfi,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                  12849  0 
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
k10temp                12990  0 
soundcore              14635  1 snd
parport_pc             32114  1 
mac_hid                13077  0 
asus_atk0110           17742  0 
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
wmi                    18744  0 
i2c_piix4              13093  0 
btcx_risc              13400  2 cx8800,cx88xx
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  66 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
binfmt_misc            17292  1 
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
pata_atiixp            12999  4 
r8169                  56321  0 
sata_sil24             17794  1 
ati_agp                13242  0 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    3983980     140196          0     670720    1913180
-/+ buffers/cache:    1400080    2724096
Swap:     11829568        172   11829396

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable suspend suspend:

/etc/pm/sleep.d/95_zram_disable suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Wed Nov 14 22:40:03 CET 2012: performing suspend
Thu Nov 15 04:28:31 CET 2012: Awake.
Thu Nov 15 04:28:31 CET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable resume suspend:

/etc/pm/sleep.d/95_zram_disable resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Thu Nov 15 04:28:32 CET 2012: Finished.
Initial commandline parameters: 
Thu Nov 15 23:14:37 CET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
decnet                 66360  0 [permanent]
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
dm_crypt               22528  5 
snd_hda_codec_via      46138  1 
snd_hda_intel          32765  4 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
snd_ctxfi              86200  2 
snd_hwdep              13276  1 snd_hda_codec
tda9887                17874  1 
snd_pcm                80845  4 snd_hda_intel,snd_hda_codec,snd_ctxfi
ir_lirc_codec          12739  0 
tda8290                22216  0 
lirc_dev               18700  1 ir_lirc_codec
snd_seq_midi           13132  0 
ir_mce_kbd_decoder     12681  0 
ir_sony_decoder        12462  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
tea5767                13113  0 
ir_jvc_decoder         12459  0 
tuner                  26836  2 
snd_timer              28931  2 snd_pcm,snd_seq
ir_rc6_decoder         12459  0 
ir_rc5_decoder         12459  0 
ir_nec_decoder         12459  0 
sp5100_tco             13495  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cx8800                 33328  0 
cx88xx                 83089  1 cx8800
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
serio_raw              13027  0 
snd                    62064  21 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_ctxfi,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videobuf_dma_sg        18786  2 cx8800,cx88xx
dm_multipath           22710  0 
ppdev                  12849  0 
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              14635  1 snd
parport_pc             32114  1 
mac_hid                13077  0 
i2c_piix4              13093  0 
btcx_risc              13400  2 cx8800,cx88xx
k10temp                12990  0 
adt7475                21887  0 
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
asus_atk0110           17742  0 
wmi                    18744  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  60 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
binfmt_misc            17292  1 
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
pata_atiixp            12999  4 
sata_sil24             17794  1 
r8169                  56321  0 
ati_agp                13242  0 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    3943228     180948          0     649756    1860656
-/+ buffers/cache:    1432816    2691360
Swap:     11829568       4356   11825212

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable suspend suspend:

/etc/pm/sleep.d/95_zram_disable suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Nov 15 23:14:41 CET 2012: performing suspend
Fri Nov 16 04:28:46 CET 2012: Awake.
Fri Nov 16 04:28:46 CET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable resume suspend:

/etc/pm/sleep.d/95_zram_disable resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Fri Nov 16 04:28:47 CET 2012: Finished.
Initial commandline parameters: 
Sat Nov 17 21:18:30 CET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
decnet                 66360  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22528  5 
tda9887                17874  1 
snd_hda_codec_via      46138  1 
tda8290                22216  0 
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
tea5767                13113  0 
ir_mce_kbd_decoder     12681  0 
ir_sony_decoder        12462  0 
snd_hda_intel          32765  3 
ir_jvc_decoder         12459  0 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
snd_ctxfi              86200  2 
ir_rc6_decoder         12459  0 
tuner                  26836  2 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_intel,snd_hda_codec,snd_ctxfi
ir_rc5_decoder         12459  0 
ir_nec_decoder         12459  0 
cx8800                 33328  0 
cx88xx                 83089  1 cx8800
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
v4l2_common            15793  3 tuner,cx8800,cx88xx
snd_timer              28931  2 snd_pcm,snd_seq
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
sp5100_tco             13495  0 
serio_raw              13027  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  20 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_ctxfi,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
dm_multipath           22710  0 
ppdev                  12849  0 
soundcore              14635  1 snd
parport_pc             32114  1 
mac_hid                13077  0 
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
asus_atk0110           17742  0 
k10temp                12990  0 
i2c_piix4              13093  0 
wmi                    18744  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  50 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
pata_atiixp            12999  4 
sata_sil24             17794  1 
r8169                  56321  0 
ati_agp                13242  0 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    3871276     252900          0     623236    2128856
-/+ buffers/cache:    1119184    3004992
Swap:     11829568       1864   11827704

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable suspend suspend:

/etc/pm/sleep.d/95_zram_disable suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sat Nov 17 21:18:33 CET 2012: performing suspend
Sat Nov 17 21:42:37 CET 2012: Awake.
Sat Nov 17 21:42:37 CET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable resume suspend:

/etc/pm/sleep.d/95_zram_disable resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Sat Nov 17 21:42:38 CET 2012: Finished.
Initial commandline parameters: 
Sun Nov 18 03:07:14 CET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
decnet                 66360  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22528  5 
tda9887                17874  1 
snd_hda_codec_via      46138  1 
tda8290                22216  0 
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
tea5767                13113  0 
ir_mce_kbd_decoder     12681  0 
ir_sony_decoder        12462  0 
snd_hda_intel          32765  4 
ir_jvc_decoder         12459  0 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
snd_ctxfi              86200  2 
ir_rc6_decoder         12459  0 
tuner                  26836  2 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  4 snd_hda_intel,snd_hda_codec,snd_ctxfi
ir_rc5_decoder         12459  0 
ir_nec_decoder         12459  0 
cx8800                 33328  0 
cx88xx                 83089  1 cx8800
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
v4l2_common            15793  3 tuner,cx8800,cx88xx
snd_timer              28931  2 snd_pcm,snd_seq
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
sp5100_tco             13495  0 
serio_raw              13027  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  21 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_ctxfi,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
dm_multipath           22710  0 
ppdev                  12849  0 
soundcore              14635  1 snd
parport_pc             32114  1 
mac_hid                13077  0 
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
asus_atk0110           17742  0 
k10temp                12990  0 
i2c_piix4              13093  0 
wmi                    18744  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  58 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
pata_atiixp            12999  4 
sata_sil24             17794  1 
r8169                  56321  0 
ati_agp                13242  0 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    3618024     506152          0     630796    1867440
-/+ buffers/cache:    1119788    3004388
Swap:     11829568      14076   11815492

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable suspend suspend:

/etc/pm/sleep.d/95_zram_disable suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sun Nov 18 03:07:17 CET 2012: performing suspend
Sun Nov 18 09:02:25 CET 2012: Awake.
Sun Nov 18 09:02:25 CET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable resume suspend:

/etc/pm/sleep.d/95_zram_disable resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Sun Nov 18 09:02:26 CET 2012: Finished.
Initial commandline parameters: 
Sun Nov 18 22:51:39 CET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
decnet                 66360  0 [permanent]
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
dm_crypt               22528  5 
tda9887                17874  1 
snd_hda_codec_via      46138  1 
tda8290                22216  0 
tea5767                13113  0 
snd_hda_intel          32765  4 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_ctxfi              86200  2 
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
snd_pcm                80845  4 snd_hda_intel,snd_hda_codec,snd_ctxfi
ir_mce_kbd_decoder     12681  0 
snd_seq_midi           13132  0 
ir_sony_decoder        12462  0 
tuner                  26836  2 
ir_jvc_decoder         12459  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
cx8800                 33328  0 
ir_rc6_decoder         12459  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ir_rc5_decoder         12459  0 
cx88xx                 83089  1 cx8800
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ir_nec_decoder         12459  0 
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,cx88xx,ir_nec_decoder
i2c_algo_bit           13199  1 cx88xx
snd                    62064  21 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
ppdev                  12849  0 
tveeprom               17009  1 cx88xx
v4l2_common            15793  3 tuner,cx8800,cx88xx
soundcore              14635  1 snd
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
serio_raw              13027  0 
dm_multipath           22710  0 
parport_pc             32114  1 
mac_hid                13077  0 
asus_atk0110           17742  0 
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
k10temp                12990  0 
wmi                    18744  0 
btcx_risc              13400  2 cx8800,cx88xx
i2c_piix4              13093  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  54 
lp                     17455  0 
binfmt_misc            17292  1 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
pata_atiixp            12999  4 
sata_sil24             17794  1 
ati_agp                13242  0 
r8169                  56321  0 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    3723600     400576          0     668344    1863228
-/+ buffers/cache:    1192028    2932148
Swap:     11829568          0   11829568

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable suspend suspend:

/etc/pm/sleep.d/95_zram_disable suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sun Nov 18 22:51:42 CET 2012: performing suspend
Mon Nov 19 09:29:33 CET 2012: Awake.
Mon Nov 19 09:29:33 CET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable resume suspend:

/etc/pm/sleep.d/95_zram_disable resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Mon Nov 19 09:29:34 CET 2012: Finished.
Initial commandline parameters: 
Tue Nov 20 00:24:09 CET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
dm_crypt               22528  5 
decnet                 66360  0 [permanent]
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
tda9887                17874  1 
tda8290                22216  0 
tea5767                13113  0 
ir_lirc_codec          12739  0 
snd_hda_codec_via      46138  1 
tuner                  26836  2 
snd_hda_intel          32765  4 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
lirc_dev               18700  1 ir_lirc_codec
cx8800                 33328  0 
snd_hwdep              13276  1 snd_hda_codec
ir_mce_kbd_decoder     12681  0 
snd_ctxfi              86200  2 
snd_pcm                80845  4 snd_hda_intel,snd_hda_codec,snd_ctxfi
ir_sony_decoder        12462  0 
cx88xx                 83089  1 cx8800
snd_seq_midi           13132  0 
ir_jvc_decoder         12459  0 
ir_rc6_decoder         12459  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ir_rc5_decoder         12459  0 
sp5100_tco             13495  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ir_nec_decoder         12459  0 
dm_multipath           22710  0 
ppdev                  12849  0 
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,cx88xx,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  21 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13027  0 
parport_pc             32114  1 
mac_hid                13077  0 
btcx_risc              13400  2 cx8800,cx88xx
k10temp                12990  0 
asus_atk0110           17742  0 
soundcore              14635  1 snd
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
i2c_piix4              13093  0 
wmi                    18744  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  50 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
binfmt_misc            17292  1 
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
sata_sil24             17794  1 
ati_agp                13242  0 
r8169                  56321  0 
pata_atiixp            12999  4 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    3964120     160056          0     673012    2190652
-/+ buffers/cache:    1100456    3023720
Swap:     11829568          0   11829568

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable suspend suspend:

/etc/pm/sleep.d/95_zram_disable suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Tue Nov 20 00:24:12 CET 2012: performing suspend
Tue Nov 20 09:29:34 CET 2012: Awake.
Tue Nov 20 09:29:34 CET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable resume suspend:

/etc/pm/sleep.d/95_zram_disable resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Tue Nov 20 09:29:34 CET 2012: Finished.
Initial commandline parameters: 
Wed Nov 21 01:02:50 CET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
decnet                 66360  0 [permanent]
dm_crypt               22528  5 
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
ir_mce_kbd_decoder     12681  0 
snd_hda_codec_via      46138  1 
ir_sony_decoder        12462  0 
snd_hda_intel          32765  4 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
snd_ctxfi              86200  2 
ir_jvc_decoder         12459  0 
tda9887                17874  1 
snd_hwdep              13276  1 snd_hda_codec
ir_rc6_decoder         12459  0 
tda8290                22216  0 
snd_pcm                80845  4 snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_seq_midi           13132  0 
ir_rc5_decoder         12459  0 
tea5767                13113  0 
tuner                  26836  2 
ir_nec_decoder         12459  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
cx8800                 33328  0 
cx88xx                 83089  1 cx8800
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
tveeprom               17009  1 cx88xx
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
v4l2_common            15793  3 tuner,cx8800,cx88xx
sp5100_tco             13495  0 
ppdev                  12849  0 
dm_multipath           22710  0 
snd                    62064  21 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_ctxfi,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
btcx_risc              13400  2 cx8800,cx88xx
soundcore              14635  1 snd
serio_raw              13027  0 
parport_pc             32114  1 
mac_hid                13077  0 
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
k10temp                12990  0 
wmi                    18744  0 
asus_atk0110           17742  0 
i2c_piix4              13093  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  50 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
binfmt_misc            17292  1 
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
sata_sil24             17794  1 
pata_atiixp            12999  4 
r8169                  56321  0 
ati_agp                13242  0 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    3977308     146868          0     674476    2144252
-/+ buffers/cache:    1158580    2965596
Swap:     11829568        248   11829320

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable suspend suspend:

/etc/pm/sleep.d/95_zram_disable suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Wed Nov 21 01:02:53 CET 2012: performing suspend
Wed Nov 21 09:29:48 CET 2012: Awake.
Wed Nov 21 09:29:48 CET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable resume suspend:

/etc/pm/sleep.d/95_zram_disable resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Wed Nov 21 09:29:49 CET 2012: Finished.
Initial commandline parameters: 
Thu Nov 22 01:07:02 CET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
decnet                 66360  0 [permanent]
dm_crypt               22528  5 
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
snd_hda_codec_via      46138  1 
tda9887                17874  1 
snd_hda_intel          32765  4 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
ir_lirc_codec          12739  0 
tda8290                22216  0 
lirc_dev               18700  1 ir_lirc_codec
tea5767                13113  0 
snd_ctxfi              86200  2 
snd_pcm                80845  4 snd_hda_intel,snd_hda_codec,snd_ctxfi
ir_mce_kbd_decoder     12681  0 
tuner                  26836  2 
snd_seq_midi           13132  0 
ir_sony_decoder        12462  0 
snd_rawmidi            25424  1 snd_seq_midi
ir_jvc_decoder         12459  0 
snd_seq_midi_event     14475  1 snd_seq_midi
ir_rc6_decoder         12459  0 
cx8800                 33328  0 
ir_rc5_decoder         12459  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ir_nec_decoder         12459  0 
cx88xx                 83089  1 cx8800
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
snd                    62064  21 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dm_multipath           22710  0 
sp5100_tco             13495  0 
ppdev                  12849  0 
soundcore              14635  1 snd
serio_raw              13027  0 
parport_pc             32114  1 
mac_hid                13077  0 
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
btcx_risc              13400  2 cx8800,cx88xx
asus_atk0110           17742  0 
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
i2c_piix4              13093  0 
wmi                    18744  0 
k10temp                12990  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  50 
binfmt_misc            17292  1 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
pata_atiixp            12999  4 
r8169                  56321  0 
sata_sil24             17794  1 
ati_agp                13242  0 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    3983868     140308          0     674664    2170172
-/+ buffers/cache:    1139032    2985144
Swap:     11829568        360   11829208

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable suspend suspend:

/etc/pm/sleep.d/95_zram_disable suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Nov 22 01:07:05 CET 2012: performing suspend
Thu Nov 22 09:29:42 CET 2012: Awake.
Thu Nov 22 09:29:42 CET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable resume suspend:

/etc/pm/sleep.d/95_zram_disable resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Thu Nov 22 09:29:43 CET 2012: Finished.
Initial commandline parameters: 
Fri Nov 23 04:40:02 CET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
dm_crypt               22528  5 
decnet                 66360  0 [permanent]
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
snd_hda_codec_via      46138  1 
tda9887                17874  1 
snd_hda_intel          32765  4 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
ir_mce_kbd_decoder     12681  0 
snd_ctxfi              86200  2 
tda8290                22216  0 
ir_sony_decoder        12462  0 
ir_jvc_decoder         12459  0 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  4 snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_seq_midi           13132  0 
tea5767                13113  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ir_rc6_decoder         12459  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
tuner                  26836  2 
ir_rc5_decoder         12459  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  21 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_ctxfi,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
dm_multipath           22710  0 
ir_nec_decoder         12459  0 
ppdev                  12849  0 
cx8800                 33328  0 
cx88xx                 83089  1 cx8800
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              14635  1 snd
serio_raw              13027  0 
parport_pc             32114  1 
mac_hid                13077  0 
i2c_piix4              13093  0 
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
asus_atk0110           17742  0 
wmi                    18744  0 
k10temp                12990  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  50 
binfmt_misc            17292  1 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
pata_atiixp            12999  4 
r8169                  56321  0 
ati_agp                13242  0 
sata_sil24             17794  1 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    3999324     124852          0     669364    1682668
-/+ buffers/cache:    1647292    2476884
Swap:     11829568     114644   11714924

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable suspend suspend:

/etc/pm/sleep.d/95_zram_disable suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Nov 23 04:40:07 CET 2012: performing suspend
Fri Nov 23 11:25:24 CET 2012: Awake.
Fri Nov 23 11:25:24 CET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable resume suspend:

/etc/pm/sleep.d/95_zram_disable resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Fri Nov 23 11:25:25 CET 2012: Finished.
Initial commandline parameters: 
Fri Nov 23 12:26:38 CET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55605  1 vfat
uas                    17828  0 
usb_storage            39646  0 
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
dm_crypt               22528  5 
decnet                 66360  0 [permanent]
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
snd_hda_codec_via      46138  1 
tda9887                17874  1 
snd_hda_intel          32765  4 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
ir_mce_kbd_decoder     12681  0 
snd_ctxfi              86200  2 
tda8290                22216  0 
ir_sony_decoder        12462  0 
ir_jvc_decoder         12459  0 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  4 snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_seq_midi           13132  0 
tea5767                13113  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ir_rc6_decoder         12459  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
tuner                  26836  2 
ir_rc5_decoder         12459  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  21 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_ctxfi,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
dm_multipath           22710  0 
ir_nec_decoder         12459  0 
ppdev                  12849  0 
cx8800                 33328  0 
cx88xx                 83089  1 cx8800
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              14635  1 snd
serio_raw              13027  0 
parport_pc             32114  1 
mac_hid                13077  0 
i2c_piix4              13093  0 
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
asus_atk0110           17742  0 
wmi                    18744  0 
k10temp                12990  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  58 
binfmt_misc            17292  1 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
pata_atiixp            12999  4 
r8169                  56321  0 
ati_agp                13242  0 
sata_sil24             17794  1 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    3866092     258084          0     549880    1633692
-/+ buffers/cache:    1682520    2441656
Swap:     11829568      96908   11732660

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable suspend suspend:

/etc/pm/sleep.d/95_zram_disable suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Nov 23 12:26:41 CET 2012: performing suspend
Fri Nov 23 15:20:19 CET 2012: Awake.
Fri Nov 23 15:20:19 CET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable resume suspend:

/etc/pm/sleep.d/95_zram_disable resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Fri Nov 23 15:20:20 CET 2012: Finished.
Initial commandline parameters: 
Fri Nov 23 15:55:42 CET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55605  1 vfat
uas                    17828  0 
usb_storage            39646  0 
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
dm_crypt               22528  5 
decnet                 66360  0 [permanent]
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
snd_hda_codec_via      46138  1 
tda9887                17874  1 
snd_hda_intel          32765  4 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
ir_mce_kbd_decoder     12681  0 
snd_ctxfi              86200  2 
tda8290                22216  0 
ir_sony_decoder        12462  0 
ir_jvc_decoder         12459  0 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  4 snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_seq_midi           13132  0 
tea5767                13113  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ir_rc6_decoder         12459  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
tuner                  26836  2 
ir_rc5_decoder         12459  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  21 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_ctxfi,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
dm_multipath           22710  0 
ir_nec_decoder         12459  0 
ppdev                  12849  0 
cx8800                 33328  0 
cx88xx                 83089  1 cx8800
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              14635  1 snd
serio_raw              13027  0 
parport_pc             32114  1 
mac_hid                13077  0 
i2c_piix4              13093  0 
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
asus_atk0110           17742  0 
wmi                    18744  0 
k10temp                12990  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  58 
binfmt_misc            17292  1 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
pata_atiixp            12999  4 
r8169                  56321  0 
ati_agp                13242  0 
sata_sil24             17794  1 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    3741912     382264          0     437708    1552108
-/+ buffers/cache:    1752096    2372080
Swap:     11829568      96860   11732708

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable suspend suspend:

/etc/pm/sleep.d/95_zram_disable suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Nov 23 15:55:44 CET 2012: performing suspend
Fri Nov 23 16:18:24 CET 2012: Awake.
Fri Nov 23 16:18:24 CET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable resume suspend:

/etc/pm/sleep.d/95_zram_disable resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Fri Nov 23 16:18:24 CET 2012: Finished.
Initial commandline parameters: 
pi&#261;, 23 lis 2012, 19:44:17 CET: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55605  1 vfat
uas                    17828  0 
usb_storage            39646  0 
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
dm_crypt               22528  5 
decnet                 66360  0 [permanent]
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
snd_hda_codec_via      46138  1 
tda9887                17874  1 
snd_hda_intel          32765  4 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
ir_mce_kbd_decoder     12681  0 
snd_ctxfi              86200  2 
tda8290                22216  0 
ir_sony_decoder        12462  0 
ir_jvc_decoder         12459  0 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  4 snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_seq_midi           13132  0 
tea5767                13113  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ir_rc6_decoder         12459  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
tuner                  26836  2 
ir_rc5_decoder         12459  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  21 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_ctxfi,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
dm_multipath           22710  0 
ir_nec_decoder         12459  0 
ppdev                  12849  0 
cx8800                 33328  0 
cx88xx                 83089  1 cx8800
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              14635  1 snd
serio_raw              13027  0 
parport_pc             32114  1 
mac_hid                13077  0 
i2c_piix4              13093  0 
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
asus_atk0110           17742  0 
wmi                    18744  0 
k10temp                12990  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  58 
binfmt_misc            17292  1 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
pata_atiixp            12999  4 
r8169                  56321  0 
ati_agp                13242  0 
sata_sil24             17794  1 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    3743520     380656          0     562168    1188628
-/+ buffers/cache:    1992724    2131452
Swap:     11829568     104532   11725036

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable suspend suspend:

/etc/pm/sleep.d/95_zram_disable suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
pi&#261;, 23 lis 2012, 19:44:20 CET: performing suspend
pi&#261;, 23 lis 2012, 19:44:44 CET: Awake.
pi&#261;, 23 lis 2012, 19:44:44 CET: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable resume suspend:

/etc/pm/sleep.d/95_zram_disable resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
pi&#261;, 23 lis 2012, 19:44:44 CET: Finished.
Initial commandline parameters: 
pi&#261;, 23 lis 2012, 19:45:09 CET: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55605  1 vfat
uas                    17828  0 
usb_storage            39646  0 
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
dm_crypt               22528  5 
decnet                 66360  0 [permanent]
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
snd_hda_codec_via      46138  1 
tda9887                17874  1 
snd_hda_intel          32765  4 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
ir_mce_kbd_decoder     12681  0 
snd_ctxfi              86200  2 
tda8290                22216  0 
ir_sony_decoder        12462  0 
ir_jvc_decoder         12459  0 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  4 snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_seq_midi           13132  0 
tea5767                13113  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ir_rc6_decoder         12459  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
tuner                  26836  2 
ir_rc5_decoder         12459  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  21 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_ctxfi,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
dm_multipath           22710  0 
ir_nec_decoder         12459  0 
ppdev                  12849  0 
cx8800                 33328  0 
cx88xx                 83089  1 cx8800
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              14635  1 snd
serio_raw              13027  0 
parport_pc             32114  1 
mac_hid                13077  0 
i2c_piix4              13093  0 
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
asus_atk0110           17742  0 
wmi                    18744  0 
k10temp                12990  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  62 
binfmt_misc            17292  1 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
pata_atiixp            12999  4 
r8169                  56321  0 
ati_agp                13242  0 
sata_sil24             17794  1 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    3889804     234372          0     603316    1257880
-/+ buffers/cache:    2028608    2095568
Swap:     11829568     104532   11725036

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable hibernate hibernate:
umount: /dev/zram0: nie jest zamontowane

/etc/pm/sleep.d/95_zram_disable hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
pi&#261;, 23 lis 2012, 19:45:14 CET: performing hibernate
pi&#261;, 23 lis 2012, 19:45:37 CET: Awake.
pi&#261;, 23 lis 2012, 19:45:37 CET: Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:

/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:

/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable thaw hibernate:
Tworzenie obszaru wymiany w wersji 1, rozmiar = 1031036 KiB
brak etykiety, UUID=80548b2c-1854-4b29-be07-28a93ff542ce

/etc/pm/sleep.d/95_zram_disable thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:

/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:

/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:

/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:

/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
pi&#261;, 23 lis 2012, 19:45:38 CET: Finished.
Initial commandline parameters: 
Fri Nov 23 19:45:45 CET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55605  1 vfat
uas                    17828  0 
usb_storage            39646  0 
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
dm_crypt               22528  5 
decnet                 66360  0 [permanent]
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
snd_hda_codec_via      46138  1 
tda9887                17874  1 
snd_hda_intel          32765  4 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
ir_mce_kbd_decoder     12681  0 
snd_ctxfi              86200  2 
tda8290                22216  0 
ir_sony_decoder        12462  0 
ir_jvc_decoder         12459  0 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  4 snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_seq_midi           13132  0 
tea5767                13113  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ir_rc6_decoder         12459  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
tuner                  26836  2 
ir_rc5_decoder         12459  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  21 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_ctxfi,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
dm_multipath           22710  0 
ir_nec_decoder         12459  0 
ppdev                  12849  0 
cx8800                 33328  0 
cx88xx                 83089  1 cx8800
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              14635  1 snd
serio_raw              13027  0 
parport_pc             32114  1 
mac_hid                13077  0 
i2c_piix4              13093  0 
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
asus_atk0110           17742  0 
wmi                    18744  0 
k10temp                12990  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
nvidia              10962290  62 
binfmt_misc            17292  1 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
usbhid                 41906  0 
hid                    77392  1 usbhid
sundance               26629  0 
pata_atiixp            12999  4 
r8169                  56321  0 
ati_agp                13242  0 
sata_sil24             17794  1 
zram                   18193  1 
             total       used       free     shared    buffers     cached
Mem:       4124176    3897092     227084          0     595548    1243232
-/+ buffers/cache:    2058312    2065864
Swap:     10798520          0   10798520

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable suspend suspend:

/etc/pm/sleep.d/95_zram_disable suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Nov 23 19:45:46 CET 2012: performing suspend
Fri Nov 23 20:20:28 CET 2012: Awake.
Fri Nov 23 20:20:28 CET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable resume suspend:

/etc/pm/sleep.d/95_zram_disable resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Fri Nov 23 20:20:29 CET 2012: Finished.

```

Can you help me? I have swap enabled:
```

firekage@deusex:~$ sudo blkid 
/dev/sda1: UUID="9a4b8b62" TYPE="swap" 
/dev/zram0: UUID="80548b2c" TYPE="swap" 


```

Maybe it is related to this "fake swap" labeled as zram0 - i don't know why it is, what installed it (if) and what to do to be sure that sda1 is partition for swap, and only it.

---

### Post by firekage on 2012-11-25
Help?

---

### Post by personalpc on 2012-11-25
What does your /etc/default/grub file have for acpi? Make sure it wasn't installed with the noacpi or acpi=off variables. 

Also what is the make and model of the PC. A lot of different manufactures use proprietary acpi statements for the integration of custom buttons such as the ones found on laptops.

---

### Post by Toz on 2012-11-25
According to your log files, suspend works but hibernate does not. And yes, zram is known to prevent hibernate from working. For hibernate, trying stopping the zram service:
```
sudo service zram stop
```
...or
```
sudo service zram-config stop
```
...then trying to hibernate. (Don't be surprised if it doesn't work as you might then run into the same problem that suspend is experiencing).

To troubleshoot the suspend, in addition to providing the information that @personalpc has requested, can you also post back (after an attempted suspend) the results of:
```
cat /proc/cmdline
cat /var/log/syslog | grep PM:
sudo lspci -vnn | grep -A12 VGA
```
...and the links that are generated by running the following commands:
```
pastebinit /var/log/pm-suspend.log
pastebinit /var/log/dmesg
```

---

### Post by firekage on 2012-12-02
> **personalpc said:**
> What does your /etc/default/grub file have for acpi? Make sure it wasn't installed with the noacpi or acpi=off variables. 

Also what is the make and model of the PC. A lot of different manufactures use proprietary acpi statements for the integration of custom buttons such as the ones found on laptops.

Here is my /etc/default/grub config file:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="resume=UUID=114c98b3-c532-42af-a84c-cbd07e97e836"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

# Grub splash images (added by me)
#GRUB_BACKGROUND="/home/firekage/SE-3D-1-narrow.png"
```


I have AMD X4 955 with 4GB of ram, nvidia GTX260 and suspend, hibernation worked before without problems.

---

### Post by firekage on 2012-12-02
> **Toz said:**
> According to your log files, suspend works but hibernate does not. And yes, zram is known to prevent hibernate from working. For hibernate, trying stopping the zram service:
```
sudo service zram stop
```...or
```
sudo service zram-config stop
```...then trying to hibernate. (Don't be surprised if it doesn't work as you might then run into the same problem that suspend is experiencing).

This is more frustrating than i thought, because:

```
firekage@deusex:/tmp$ sudo service zram stop
zram: unrecognized service
firekage@deusex:/tmp$ sudo service zram-config-stop
zram-config-stop: unrecognized service
firekage@deusex:/tmp$ 


```

If the service is unrecognized, than why i have zram? What installed it? I always have problem with it, don't know what installed it or where it came from.

> 
To troubleshoot the suspend, in addition to providing the information that @personalpc has requested, can you also post back (after an attempted suspend) the results of:
```
cat /proc/cmdline
cat /var/log/syslog | grep PM:
sudo lspci -vnn | grep -A12 VGA
```...and the links that are generated by running the following commands:
```
pastebinit /var/log/pm-suspend.log
pastebinit /var/log/dmesg
```

Ok, i will post it.

---

### Post by firekage on 2012-12-02
I suspended it, wake it up - it frozes on splash screen, don't boot. Reset, and boot again.


Here is the output of cat /proc./cmdline

```
firekage@deusex:~$ cat /proc/cmdline 
BOOT_IMAGE=/boot/vmlinuz-3.2.0-34-generic-pae root=UUID=149ac71c-7444-48aa-bc0c-9fb07bccf74c ro resume=UUID=114c98b3-c532-42af-a84c-cbd07e97e836 quiet splash
firekage@deusex:~$ 


```I see that my resume in this is not the one from sudo blkid | grep swap. I fixed it but still it doesen't work.

Here is the output of cat /var/log/syslog | grep PM

```
firekage@deusex:~$ cat /var/log/syslog | grep PM
Dec  2 11:04:53 deusex kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Dec  2 11:04:53 deusex kernel: [    0.000000] PM: Registered nosave memory: 000000000009a000 - 000000000009b000
Dec  2 11:04:53 deusex kernel: [    0.000000] PM: Registered nosave memory: 000000000009b000 - 00000000000a0000
Dec  2 11:04:53 deusex kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
Dec  2 11:04:53 deusex kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Dec  2 11:04:53 deusex kernel: [    0.064003] Performance Events: AMD PMU driver.
Dec  2 11:04:53 deusex kernel: [    0.340202] PM: Registering ACPI NVS region at cffa8000 (163840 bytes)
Dec  2 11:04:53 deusex kernel: [    0.661099] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
Dec  2 11:04:53 deusex kernel: [    0.661102] pci 0000:00:02.0: PME# disabled
Dec  2 11:04:53 deusex kernel: [    0.661154] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
Dec  2 11:04:53 deusex kernel: [    0.661157] pci 0000:00:07.0: PME# disabled
Dec  2 11:04:53 deusex kernel: [    0.661206] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
Dec  2 11:04:53 deusex kernel: [    0.661208] pci 0000:00:0a.0: PME# disabled
Dec  2 11:04:53 deusex kernel: [    0.661638] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Dec  2 11:04:53 deusex kernel: [    0.661642] pci 0000:00:12.2: PME# disabled
Dec  2 11:04:53 deusex kernel: [    0.661931] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Dec  2 11:04:53 deusex kernel: [    0.661935] pci 0000:00:13.2: PME# disabled
Dec  2 11:04:53 deusex kernel: [    0.662262] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Dec  2 11:04:53 deusex kernel: [    0.662266] pci 0000:00:14.2: PME# disabled
Dec  2 11:04:53 deusex kernel: [    0.668308] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Dec  2 11:04:53 deusex kernel: [    0.668466] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec  2 11:04:53 deusex kernel: [    0.668470] pci 0000:03:00.0: PME# disabled
Dec  2 11:04:53 deusex kernel: [    0.676397] pci 0000:04:06.0: PME# supported from D1 D2 D3hot D3cold
Dec  2 11:04:53 deusex kernel: [    0.676402] pci 0000:04:06.0: PME# disabled
Dec  2 11:04:53 deusex kernel: [    0.676943] ACPI _OSC control for PCIe not granted, disabling ASPM
Dec  2 11:04:53 deusex kernel: [    2.141839] PM: Checking hibernation image partition UUID=114c98b3-c532-42af-a84c-cbd07e97e836
Dec  2 11:04:53 deusex kernel: [    2.453652] PM: Hibernation image not present or could not be loaded.
Dec  2 11:04:53 deusex kernel: [   16.746218] PM: Marking nosave pages: 000000000009a000 - 0000000000100000
Dec  2 11:04:53 deusex kernel: [   16.746221] PM: Basic memory bitmaps created
Dec  2 11:04:53 deusex kernel: [   16.759889] PM: Basic memory bitmaps freed
Dec  2 11:07:11 deusex kernel: [  152.002320] PM: Marking nosave pages: 000000000009a000 - 0000000000100000
Dec  2 11:07:11 deusex kernel: [  152.002325] PM: Basic memory bitmaps created
Dec  2 11:10:25 deusex kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Dec  2 11:10:25 deusex kernel: [    0.000000] PM: Registered nosave memory: 000000000009a000 - 000000000009b000
Dec  2 11:10:25 deusex kernel: [    0.000000] PM: Registered nosave memory: 000000000009b000 - 00000000000a0000
Dec  2 11:10:25 deusex kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
Dec  2 11:10:25 deusex kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Dec  2 11:10:25 deusex kernel: [    0.064003] Performance Events: AMD PMU driver.
Dec  2 11:10:25 deusex kernel: [    0.340203] PM: Registering ACPI NVS region at cffa8000 (163840 bytes)
Dec  2 11:10:25 deusex kernel: [    0.645090] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
Dec  2 11:10:25 deusex kernel: [    0.645093] pci 0000:00:02.0: PME# disabled
Dec  2 11:10:25 deusex kernel: [    0.645145] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
Dec  2 11:10:25 deusex kernel: [    0.645148] pci 0000:00:07.0: PME# disabled
Dec  2 11:10:25 deusex kernel: [    0.645197] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
Dec  2 11:10:25 deusex kernel: [    0.645199] pci 0000:00:0a.0: PME# disabled
Dec  2 11:10:25 deusex kernel: [    0.645630] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Dec  2 11:10:25 deusex kernel: [    0.645633] pci 0000:00:12.2: PME# disabled
Dec  2 11:10:25 deusex kernel: [    0.645922] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Dec  2 11:10:25 deusex kernel: [    0.645926] pci 0000:00:13.2: PME# disabled
Dec  2 11:10:25 deusex kernel: [    0.646254] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Dec  2 11:10:25 deusex kernel: [    0.646258] pci 0000:00:14.2: PME# disabled
Dec  2 11:10:25 deusex kernel: [    0.652303] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Dec  2 11:10:25 deusex kernel: [    0.652461] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec  2 11:10:25 deusex kernel: [    0.652464] pci 0000:03:00.0: PME# disabled
Dec  2 11:10:25 deusex kernel: [    0.660408] pci 0000:04:06.0: PME# supported from D1 D2 D3hot D3cold
Dec  2 11:10:25 deusex kernel: [    0.660413] pci 0000:04:06.0: PME# disabled
Dec  2 11:10:25 deusex kernel: [    0.660979] ACPI _OSC control for PCIe not granted, disabling ASPM
Dec  2 11:10:25 deusex kernel: [    2.085832] PM: Checking hibernation image partition UUID=114c98b3-c532-42af-a84c-cbd07e97e836
Dec  2 11:10:25 deusex kernel: [    2.389562] PM: Hibernation image not present or could not be loaded.
Dec  2 11:10:25 deusex kernel: [   16.849721] PM: Marking nosave pages: 000000000009a000 - 0000000000100000
Dec  2 11:10:25 deusex kernel: [   16.849725] PM: Basic memory bitmaps created
Dec  2 11:10:25 deusex kernel: [   16.863353] PM: Basic memory bitmaps freed
firekage@deusex:~$ 

```Here is the output of lspci (don't know what -vnn and A12 mean)

```
firekage@deusex:~$ sudo lspci -vnn | grep -A12 VGA
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GT200 [GeForce GTX 260] [10de:05e2] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Giga-byte Technology Device [1458:34c8]
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at f4000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at bc00 [size=128]
    [virtual] Expansion ROM at f7d80000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
firekage@deusex:~$ 

```And here is something more, i tried to update initramfs, and..

```
firekage@deusex:/$ sudo update-initramfs -u -k all
update-initramfs: Generating /boot/initrd.img-3.2.0-34-generic-pae
cryptsetup: WARNING: failed to detect canonical device of /dev/sda1
update-initramfs: Generating /boot/initrd.img-3.2.0-33-generic-pae
cryptsetup: WARNING: failed to detect canonical device of /dev/sda1
update-initramfs: Generating /boot/initrd.img-3.2.0-32-generic-pae
cryptsetup: WARNING: failed to detect canonical device of /dev/sda1
update-initramfs: Generating /boot/initrd.img-3.2.0-31-generic-pae
cryptsetup: WARNING: failed to detect canonical device of /dev/sda1
update-initramfs: Generating /boot/initrd.img-3.2.0-30-generic-pae
cryptsetup: WARNING: failed to detect canonical device of /dev/sda1
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic-pae
cryptsetup: WARNING: failed to detect canonical device of /dev/sda1
update-initramfs: Generating /boot/initrd.img-3.2.0-27-generic-pae
cryptsetup: WARNING: failed to detect canonical device of /dev/sda1
update-initramfs: Generating /boot/initrd.img-3.0.0-16-generic-pae
cryptsetup: WARNING: failed to detect canonical device of /dev/sda1


```Could you help me? Thanks :)

---

### Post by firekage on 2012-12-02
.

---

### Post by firekage on 2012-12-02
Here are the links:

[http://paste.ubuntu.com/1404256/](http://paste.ubuntu.com/1404256/)

[http://paste.ubuntu.com/1404261/](http://paste.ubuntu.com/1404261/)

BTW, i found this:

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

and it is what they wrote in it:

> 
Making the swap partition work for hibernate (optional) 
**'INFO: This will not work for 12.04, resume from hibernate work differently in 12.04.**' 

[LIST=1]
[*]Pull up a Terminal again and run cat /proc/swaps  and hopefully you see the path to your swap partition listed there. If  not chances are something went wrong in the steps above. Here's my  output: 
[/LIST]

Filename                                Type            Size    Used    Priority /dev/sda2                               partition       2676732 73380   -1
[LIST=1]
[*]gksu gedit /etc/default/grub & to pull up the boot loader configuration 
[*]Look for the line GRUB_CMDLINE_LINUX="" and make sure it looks like this (using your UUID of course) GRUB_CMDLINE_LINUX="resume=UUID=41e86209-3802-424b-9a9d-d7683142dab7" and save the file 
[*]sudo update-grub and wait for it to finish 
[*]gksu gedit /etc/initramfs-tools/conf.d/resume & and make sure its contents are resume=UUID=41e86209-3802-424b-9a9d-d7683142dab7 (with your UUID of course in place of mine). Save the file! 
[*]sudo update-initramfs -u 
[*]Reboot! 
[/LIST]
Now you should be able to hibernate and resume! 

I remember that it worked before. Now i see that for 12.04 it doesen't?!

---

### Post by Toz on 2012-12-02
> **firekage said:**
> This is more frustrating than i thought, because:

```

firekage@deusex:/tmp$[COLOR="Red"] sudo service zram-config-stop[/COLOR]
zram-config-stop: unrecognized service
firekage@deusex:/tmp$ 


```


Typo. No dash before stop. Try:
```
sudo service zram-config stop
```

---

### Post by firekage on 2012-12-02
> firekage@deusex:~$ sudo service zram-config stop
[sudo] password for firekage: 
zram-config: unrecognized service
firekage@deusex:~$ 


Still, the same.

---

### Post by Toz on 2012-12-02
> **firekage said:**
> Here are the links:

[http://paste.ubuntu.com/1404256/](http://paste.ubuntu.com/1404256/)

[http://paste.ubuntu.com/1404261/](http://paste.ubuntu.com/1404261/)

BTW, i found this:

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

and it is what they wrote in it:



I remember that it worked before. Now i see that for 12.04 it doesen't?!

Lets focus on suspend first. Please note that hibernate _will not_ work with an encrypted swap drive. Try disabling zram with the command in the post above and try to suspend. Afterwards, post back the results of /var/log/pm-suspend.log again.

---

### Post by Toz on 2012-12-02
> **firekage said:**
> Still, the same.

What does the following return:
```
dpkg -l | grep zram
```

---

### Post by Toz on 2012-12-02
Just looking at the package contents. Try this command to stop zram:
```
sudo invoke-rc.d zram-config stop
```

---

### Post by firekage on 2012-12-02
I did something different. 

You said to stop zram with zram-config, so i had an idea, i installed it (first i checked it with synaptic - there was package named like that, but coldn't install it from synaptic) with 

```
sudo apt-get install zram-config[/CODE

], and then i stopped it with 

[CODE]sudo service zram-config stop
```, 

and the service was luckily stopped, now with

```
 sudo blkid | grep swap 
```

i see that zram disappeared from "swap":

```

firekage@deusex:~$ sudo blkid | grep swap
/dev/sda1: UUID="9a4b8b62-9163-4d61-b9af-4d4c75e29fee" TYPE="swap" 
firekage@deusex:~$ 

```


after installation of zram-config this is the output of zram:

```
ii  zram-config                                                 0.1                                                    Upstart job to enable zram support
firekage@deusex:~$ 


```

---

### Post by firekage on 2012-12-02
> **Toz said:**
> Just looking at the package contents. Try this command to stop zram:
```
sudo invoke-rc.d zram-config stop
```

I think that it should be done from sudo service than from invoke because of this:

```
firekage@deusex:~$ sudo invode-rc.d zram-config stop
sudo: invode-rc.d: nie znaleziono polecenia
firekage@deusex:~$ sudo invoke-rc.d zram-config stop
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service zram-config stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may 
```

---

### Post by firekage on 2012-12-02
Maybe im wrong but there is something with pm-hibernate. I tried manually hibernate it with this;

[https://help.ubuntu.com/community/PowerManagement/Hibernate](https://help.ubuntu.com/community/PowerManagement/Hibernate)
> 
**swsusp**

 In  Ubuntu, the default method of hibernation is to use swsusp which is  built into the kernel. Gnome and pm-utils will use this method unless  configured otherwise.  
The way you manually trigger hibernation using this 'kernel' method is to write 'disk' to /sys/power/state. There are two modes of 'kernel' hibernation: platform and shutdown. If one does not work, you can try the other: 

```



sudo -s echo platform > /sys/power/disk echo disk > /sys/power/stateOr: 

sudo -s echo shutdown > /sys/power/disk echo disk > /sys/power/state


```i entered only, with a root privileages, "echo disk > /sys/power/state" and it hibernate and resumed ok.

I don't know what is happening.

---

### Post by Toz on 2012-12-02
With zram stopped, attempt a suspend using your normal method. Afterwards, post back /var/log/pm-suspend.log.

---

### Post by firekage on 2012-12-03
> **Toz said:**
> With zram stopped, attempt a suspend using your normal method. Afterwards, post back /var/log/pm-suspend.log.

I cant hibernate it with a normal way - i click on hibernate (right top corner with Ubuntu logo) and it looks like computer is shutting down, but in fact only screen is blocked, nothing more - i can type a password to unlock screen.

Normal way won't allow me to hibernate. This is pm-suspend from echo disk > /sys/power/state:

[http://paste.ubuntu.com/1407250/](http://paste.ubuntu.com/1407250/)

---

### Post by Toz on 2012-12-03
From your log file (my red highlighting):
> Running hook /etc/pm/sleep.d/95_zram_disable hibernate hibernate:
swapoff: /dev/zram0: swapoff failed: No such file or directory
umount: /dev/zram0: not found
/etc/pm/sleep.d/95_zram_disable: line 7: /sys/block/zram0/reset: No such file or directory

/etc/pm/sleep.d/95_zram_disable hibernate hibernate: Returned exit code 1.
Mon Dec  3 09:29:41 CET 2012: [COLOR="Red"]Inhibit found, will not perform hibernate[/COLOR]

What are the contents of /etc/pm/sleep.d/95_zram_disable? Can you try removing that file, stopping zram as per your post #14, and trying hibernating using normal methods (_not_ "echo disk > /sys/power/state")? Post back /var/log/pm-suspend.log.

What are the contents of /etc/fstab?

---

### Post by firekage on 2012-12-03
> **Toz said:**
> From your log file (my red highlighting):
What are the contents of /etc/pm/sleep.d/95_zram_disable? 


Here it is:

```
firekage@deusex:/etc/pm/sleep.d$ cat 95_zram_disable 
#!/bin/bash

case "${1}" in
    hibernate)
       swapoff /dev/zram0
       umount /dev/zram0
       echo 1 > /sys/block/zram0/reset
       ;;
    thaw)
       mkswap /dev/zram0
       swapon /dev/zram0
       ;;
esac
firekage@deusex:/etc/pm/sleep.d$ 


```


> 
Can you try removing that file, stopping zram as per your post #14, and trying hibernating using normal methods (_not_ "echo disk > /sys/power/state")? Post back /var/log/pm-suspend.log.

What are the contents of /etc/fstab?

Ok, will try.

---

### Post by firekage on 2012-12-03
Thank you for your time and guidance. After renaming 95_zram_disable to 95_zram_disable.bak and chmod -x with this file, i was able to hibernate it with the normal way and it works.

```

Initial commandline parameters: 
Mon Dec  3 23:23:11 CET 2012: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux deusex 3.2.0-34-generic-pae #53-Ubuntu SMP Thu Nov 15 11:11:12 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
nls_utf8               12493  1 
isofs                  39553  1 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             25616  0 
vboxnetflt             27211  0 
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
dm_crypt               22528  5 
decnet                 66360  0 [permanent]
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
snd_hda_codec_via      46138  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_ctxfi              86200  2 
snd_pcm                80845  3 snd_hda_intel,snd_hda_codec,snd_ctxfi
tda9887                17874  1 
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
tda8290                22216  0 
ir_mce_kbd_decoder     12681  0 
snd_seq_midi           13132  0 
ir_sony_decoder        12462  0 
tea5767                13113  0 
snd_rawmidi            25424  1 snd_seq_midi
ir_jvc_decoder         12459  0 
tuner                  26836  2 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ir_rc6_decoder         12459  0 
sp5100_tco             13495  0 
cx8800                 33328  0 
cx88xx                 83089  1 cx8800
ir_rc5_decoder         12459  0 
ir_nec_decoder         12459  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
rc_core                21263  8 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,cx88xx,ir_rc5_decoder,ir_nec_decoder
tveeprom               17009  1 cx88xx
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               86588  4 tuner,cx8800,cx88xx,v4l2_common
snd                    62064  20 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videobuf_dma_sg        18786  2 cx8800,cx88xx
soundcore              14635  1 snd
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
i2c_piix4              13093  0 
mac_hid                13077  0 
btcx_risc              13400  2 cx8800,cx88xx
ppdev                  12849  0 
dm_multipath           22710  0 
k10temp                12990  0 
adt7475                21887  0 
hwmon_vid              12723  1 adt7475
asus_atk0110           17742  0 
serio_raw              13027  0 
parport_pc             32114  1 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
binfmt_misc            17292  1 
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
nouveau               712356  4 
ttm                    65344  1 nouveau
drm_kms_helper         45466  1 nouveau
drm                   197599  6 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13199  2 cx88xx,nouveau
usbhid                 41906  0 
mxm_wmi                12859  1 nouveau
hid                    77392  1 usbhid
sundance               26629  0 
pata_atiixp            12999  4 
wmi                    18744  1 mxm_wmi
video                  19068  1 nouveau
r8169                  56321  0 
ati_agp                13242  0 
sata_sil24             17794  1 
             total       used       free     shared    buffers     cached
Mem:       4124168    1961992    2162176          0      68012     599960
-/+ buffers/cache:    1294020    2830148
Swap:      9767484      93892    9673592

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable.bak hibernate hibernate:

/etc/pm/sleep.d/95_zram_disable.bak hibernate hibernate: not executable.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Mon Dec  3 23:23:12 CET 2012: performing hibernate
Mon Dec  3 23:24:42 CET 2012: Awake.
Mon Dec  3 23:24:42 CET 2012: Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:

/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:

/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable.bak thaw hibernate:

/etc/pm/sleep.d/95_zram_disable.bak thaw hibernate: not executable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:

/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:

/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:

/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:

/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
Mon Dec  3 23:24:44 CET 2012: Finished.

```


Thank You very much! Now it works like it should be. I'm more than happy :D

---

### Post by ivotkl on 2012-12-29
> **ivotkl said:**
> My GF's PC will suspend and hibernate but has AMD  chipsets on motherboard and processor. I Believe MoBo is MSI K9  or  something alike. 1 module of DDR2 2GB Kingston and 200ish HDD, Western  Digital.

I'm heading to work, so I cannot try suggestions here, or [here](http://ubuntuforums.org/showthread.php?t=2088696&highlight=suspension+hibernation+computer+won%27t+back).

Any workaround would be appreciated.

Listed modules loaded:
```
lsmod
Module                  Size  Used by
dm_crypt               22528  0 
snd_hda_codec_hdmi     31775  1 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158479  10 rfcomm,bnep
binfmt_misc            17292  1 
ppdev                  12849  0 
snd_hda_codec_realtek   174313  1 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_hda_intel          32765  10 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
psmouse                96718  0 
snd_pcm                80916  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
serio_raw              13027  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
sp5100_tco             13495  0 
snd                    62218  29 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
i2c_piix4              13093  0 
parport_pc             32114  1 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
mac_hid                13077  0 
shpchp                 32325  0 
i2c_dev                13199  0 
k8temp                 12905  0 
f71882fg               31365  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
pata_atiixp            12999  0 
radeon                733824  3 
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197641  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13199  1 radeon
r8169                  56368  0 
ati_agp                13242  0
```

---

