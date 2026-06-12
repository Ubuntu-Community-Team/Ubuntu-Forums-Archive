---
title: "crash on resume from suspend 11.10"
date: 2012-11-18
forum: General Help
---

### Post by bilboubu on 2012-11-18
I reinstalled 11.10 as upgrading to 12.10 seemed to bork my machine. I previously had no problem suspending and resuming so I dont understand wtf has happened. The machine suspends fine but when turned back on black screen and I cannot connect to it.

How can I find the cause, here is a snippet of the pm-suspend log:

```
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux htpc 3.0.0-27-generic-pae #44-Ubuntu SMP Tue Oct 16 17:13:32 UTC 2012 i686 i686 i386 GNU/Linux
Module                  Size  Used by
rfcomm                 38408  0 
bluetooth             148869  3 rfcomm
autofs4                27924  1 
dm_crypt               22565  0 
nvidia               8569966  38 
snd_hda_codec_hdmi     31426  4 
tda18271               57596  2 
zl10039                12976  1 
em28xx_dvb             17936  0 
mt312                  17440  1 
cxd2820r               28501  3 em28xx_dvb
snd_hda_intel          28358  2 
saa7134_dvb            33358  0 
saa7134_alsa           18172  0 
videobuf_dvb           13867  1 saa7134_dvb
dvb_core               94826  3 em28xx_dvb,cxd2820r,videobuf_dvb
ir_lirc_codec          12770  0 
snd_hda_codec          91888  2 snd_hda_codec_hdmi,snd_hda_intel
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
rc_videomate_s350      12475  0 
rc_rc6_mce             12454  0 
snd_hwdep              13276  1 snd_hda_codec
ir_jvc_decoder         12490  0 
saa7134               153846  2 saa7134_dvb,saa7134_alsa
mceusb                 17602  0 
ir_rc6_decoder         12490  0 
snd_pcm                80435  5 snd_hda_codec_hdmi,snd_hda_intel,saa7134_alsa,snd_hda_codec
em28xx                 93691  1 em28xx_dvb
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
ir_rc5_decoder         12490  0 
videobuf_vmalloc       13336  1 em28xx
ir_nec_decoder         12490  0 
snd_seq_midi_event     14475  1 snd_seq_midi
rc_core                25797  13 ir_lirc_codec,ir_sony_decoder,rc_videomate_s350,rc_rc6_mce,ir_jvc_decoder,saa7134,mceusb,ir_rc6_decoder,em28xx,ir_rc5_decoder,ir_nec_decoder
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
videobuf_dma_sg        18786  3 saa7134_dvb,saa7134_alsa,saa7134
videobuf_core          25409  5 videobuf_dvb,saa7134,em28xx,videobuf_vmalloc,videobuf_dma_sg
snd                    55902  13 snd_hda_codec_hdmi,snd_hda_intel,saa7134_alsa,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63474  0 
serio_raw              12990  0 
joydev                 17393  0 
v4l2_common            15793  2 saa7134,em28xx
videodev               85626  3 saa7134,em28xx,v4l2_common
tveeprom               17009  2 saa7134,em28xx
xpad                   17828  0 
ppdev                  12849  0 
parport_pc             32114  1 
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
coretemp               13188  0 
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13516  1 
hid_logitech           17405  0 
ff_memless             12945  2 xpad,hid_logitech
usbhid                 41905  1 hid_logitech
hid                    77367  2 hid_logitech,usbhid
r8169                  47200  0 
             total       used       free     shared    buffers     cached
Mem:       4124064     351364    3772700          0      15180     159512
-/+ buffers/cache:     176672    3947392
Swap:      4192252          0    4192252

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
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
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /etc/pm/sleep.d/99lirc-resume suspend suspend:
 * Stopping remote control daemon(s): LIRC
   ...done.
Unloading lirc kernel modules

/etc/pm/sleep.d/99lirc-resume suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sun Nov 18 14:25:39 GMT 2012: performing suspend
```

---

### Post by bilboubu on 2012-11-18
does this mean anything:

cat /var/log/syslog* | grep PM:

```
Nov 18 14:05:19 htpc kernel: [    0.000000] PM: Registered nosave memory: 000000                                                                                                 00000a0000 - 00000000000f0000
Nov 18 14:05:19 htpc kernel: [    0.000000] PM: Registered nosave memory: 000000                                                                                                 00000f0000 - 0000000000100000
Nov 18 14:05:19 htpc kernel: [    0.145041] PM: Registering ACPI NVS region at c                                                                                                 fee0000 (12288 bytes)
Nov 18 14:05:19 htpc kernel: [    0.739417] PM: Hibernation image not present or                                                                                                  could not be loaded.
Nov 18 14:11:34 htpc kernel: [    0.000000] PM: Registered nosave memory: 000000                                                                                                 000009f000 - 00000000000a0000
Nov 18 14:11:34 htpc kernel: [    0.000000] PM: Registered nosave memory: 000000                                                                                                 00000a0000 - 00000000000f0000
Nov 18 14:11:34 htpc kernel: [    0.000000] PM: Registered nosave memory: 000000                                                                                                 00000f0000 - 0000000000100000
Nov 18 14:11:34 htpc kernel: [    0.145044] PM: Registering ACPI NVS region at c                                                                                                 fee0000 (12288 bytes)
Nov 18 14:11:34 htpc kernel: [    0.739419] PM: Hibernation image not present or                                                                                                  could not be loaded.
Nov 18 14:17:05 htpc kernel: [    0.000000] PM: Registered nosave memory: 000000                                                                                                 000009f000 - 00000000000a0000
Nov 18 14:17:05 htpc kernel: [    0.000000] PM: Registered nosave memory: 000000                                                                                                 00000a0000 - 00000000000f0000
Nov 18 14:17:05 htpc kernel: [    0.000000] PM: Registered nosave memory: 000000                                                                                                 00000f0000 - 0000000000100000
Nov 18 14:17:05 htpc kernel: [    0.145044] PM: Registering ACPI NVS region at c                                                                                                 fee0000 (12288 bytes)
Nov 18 14:17:05 htpc kernel: [    0.735418] PM: Hibernation image not present or                                                                                                  could not be loaded.
Nov 18 14:25:05 htpc kernel: [    0.000000] PM: Registered nosave memory: 000000                                                                                                 000009f000 - 00000000000a0000
Nov 18 14:25:05 htpc kernel: [    0.000000] PM: Registered nosave memory: 000000                                                                                                 00000a0000 - 00000000000f0000
Nov 18 14:25:05 htpc kernel: [    0.000000] PM: Registered nosave memory: 000000                                                                                                 00000f0000 - 0000000000100000
Nov 18 14:25:05 htpc kernel: [    0.145044] PM: Registering ACPI NVS region at c                                                                                                 fee0000 (12288 bytes)
Nov 18 14:25:05 htpc kernel: [    0.739417] PM: Hibernation image not present or                                                                                                  could not be loaded.
Nov 18 14:27:14 htpc kernel: [    0.000000] PM: Registered nosave memory: 000000                                                                                                 000009f000 - 00000000000a0000
Nov 18 14:27:14 htpc kernel: [    0.000000] PM: Registered nosave memory: 000000                                                                                                 00000a0000 - 00000000000f0000
Nov 18 14:27:14 htpc kernel: [    0.000000] PM: Registered nosave memory: 000000                                                                                                 00000f0000 - 0000000000100000
Nov 18 14:27:14 htpc kernel: [    0.145041] PM: Registering ACPI NVS region at c                                                                                                 fee0000 (12288 bytes)
Nov 18 14:27:14 htpc kernel: [    0.739419] PM: Hibernation image not present or                                                                                                  could not be loaded.
Nov 18 14:40:27 htpc kernel: [    0.000000] PM: Registered nosave memory: 000000                                                                                                 000009f000 - 00000000000a0000
Nov 18 14:40:27 htpc kernel: [    0.000000] PM: Registered nosave memory: 000000                                                                                                 00000a0000 - 00000000000f0000
Nov 18 14:40:27 htpc kernel: [    0.000000] PM: Registered nosave memory: 000000                                                                                                 00000f0000 - 0000000000100000
Nov 18 14:40:27 htpc kernel: [    0.149042] PM: Registering ACPI NVS region at c                                                                                                 fee0000 (12288 bytes)
Nov 18 14:40:27 htpc kernel: [    0.743411] PM: Hibernation image not present or                                                                                                  could not be loaded.

```

---

### Post by bilboubu on 2012-11-18
when i take out mu usb tv stick pctv 290e resume works, I have no idea why this is ??? when it there was no problem previously.

How can I resolve this, any ideas greatly appreciated.

---

### Post by bilboubu on 2012-11-18
bloody had to unload/reload the module for that usb stick in a suspend/reume script script!

wtf I had to do that when I never have before I do no know, if anyone had an incling please share.

---

