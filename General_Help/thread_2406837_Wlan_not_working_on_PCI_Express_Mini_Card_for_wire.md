---
title: "Wlan not working on PCI Express Mini Card for wireless LAN/WAN"
date: 2018-11-26
forum: General Help
---

### Post by hail-valdemar on 2018-11-26
After couple of days of using ubuntu on my lenovo ideapad 100-15IBD laptop my wifi sudenly stoped working after restart. It seems i have some conflicts with modules, but i dont really know how to resolve them.

[B]$ rfkill list
[/B]```

*0: ideapad_wlan: Wireless LAN*
*    Soft blocked: yes*
*    Hard blocked: no*
*1: ideapad_bluetooth: Bluetooth*
*    Soft blocked: no*
[I]    Hard blocked: no
[/I]
```

Fun thing is, that **$ lspci | grep Wireless** command says i dont have wlan card. It shows nothing.

[B]$ lspci
[/B]```

00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 5500 (rev 09)
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)
00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 (rev e3)
00:1c.2 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 (rev e3)
00:1c.4 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #5 (rev e3)
00:1d.0 USB controller: Intel Corporation Wildcat Point-LP USB EHCI Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] (rev 03)
00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 08)
03:00.0 3D controller: NVIDIA Corporation GM108M [GeForce 920MX] (rev a2)

```

**$ lsmod**
```

Module                  Size  Used by
nls_iso8859_1          16384  1
rtsx_usb_ms            20480  0
memstick               16384  1 rtsx_usb_ms
uvcvideo               86016  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 videobuf2_v4l2,uvcvideo
videodev              184320  3 videobuf2_core,videobuf2_v4l2,uvcvideo
media                  40960  2 videodev,uvcvideo
snd_hda_codec_hdmi     49152  1
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             212992  0
kvm                   598016  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
pcbc                   16384  0
aesni_intel           188416  0
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
intel_cstate           20480  0
intel_rapl_perf        16384  0
joydev                 24576  0
input_leds             16384  0
serio_raw              16384  0
snd_hda_codec_conexant    24576  1
snd_hda_codec_generic    73728  1 snd_hda_codec_conexant
lpc_ich                24576  0
snd_hda_intel          40960  8
snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
snd_hda_core           81920  5 snd_hda_codec_generic,snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_hwdep              20480  1 snd_hda_codec
snd_rawmidi            32768  1 snd_seq_midi
snd_pcm                98304  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
shpchp                 36864  0
ideapad_laptop         32768  0
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
sparse_keymap          16384  1 ideapad_laptop
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              32768  2 snd_seq,snd_pcm
mei_me                 40960  0
snd                    81920  27 snd_hda_codec_generic,snd_seq,snd_hda_codec_conexant,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_timer,snd_pcm,snd_rawmidi
mei                    90112  1 mei_me
mac_hid                16384  0
acpi_pad              180224  0
soundcore              16384  1 snd
sch_fq_codel           20480  2
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
hid_generic            16384  0
rtsx_usb_sdmmc         28672  0
usbhid                 49152  0
hid                   118784  2 usbhid,hid_generic
rtsx_usb               20480  2 rtsx_usb_sdmmc,rtsx_usb_ms
nouveau              1716224  1
i915                 1617920  32
mxm_wmi                16384  1 nouveau
ttm                   106496  1 nouveau
i2c_algo_bit           16384  2 i915,nouveau
drm_kms_helper        172032  2 i915,nouveau
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
ahci                   36864  2
sysimgblt              16384  1 drm_kms_helper
psmouse               147456  0
fb_sys_fops            16384  1 drm_kms_helper
libahci                32768  1 ahci
drm                   401408  19 drm_kms_helper,i915,ttm,nouveau
i2c_i801               28672  0
r8169                  86016  0
mii                    16384  1 r8169
video                  45056  3 ideapad_laptop,i915,nouveau
wmi                    24576  3 ideapad_laptop,mxm_wmi,nouveau

```

Is there any solution or tips?

---

