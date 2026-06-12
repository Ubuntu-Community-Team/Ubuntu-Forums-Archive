---
title: "Dell 24 Monitor not recognised after Ubuntu 18.04"
date: 2018-11-03
forum: General Help
---

### Post by antnh6 on 2018-11-03
[SIZE=1][FONT=arial]I upgraded to 18.04 a few days ago and everything was fine for the last couple of days. Last night I did a software update and now my Dell u2415 monitor is not recognised through HDMI.

laptop's a Lenovo Intel Core i7. Not sure what is needed to id the issue, so I'm just gonna dump a few things here. Any help is appreciated. Thanks yall!

**xrandr**
```

Screen 0: minimum 320 x 200, current 2048 x 1152, maximum 8192 x 8192
eDP-1 connected primary 2048x1152+0+0 (normal left inverted right x axis y axis) 294mm x 165mm
   2560x1440     59.95 +  39.77  
   1920x1440     60.00  
   1856x1392     60.01  
   1792x1344     60.01  
   2048x1152     59.99*   59.98    59.90    59.91  
   1920x1200     59.88    59.95  
   1920x1080     60.01    59.97    59.96    59.93  
   1600x1200     60.00  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1600x900      59.99    59.94    59.95    59.82  
   1280x1024     60.02  
   1440x900      59.89  
   1400x900      59.96    59.88  
   1280x960      60.00  
   1440x810      60.00    59.97  
   1368x768      59.88    59.85  
   1360x768      59.80    59.96  
   1280x800      59.99    59.97    59.81    59.91  
   1152x864      60.00  
   1280x720      60.00    59.99    59.86    59.74  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   960x540       59.96    59.99    59.63    59.82  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   864x486       59.92    59.57  
   800x512       60.17  
   700x525       59.98  
   800x450       59.95    59.82  
   640x512       60.02  
   720x450       59.89  
   700x450       59.96    59.88  
   640x480       60.00    59.94  
   720x405       59.51    58.99  
   684x384       59.88    59.85  
   680x384       59.80    59.96  
   640x400       59.88    59.98  
   576x432       60.06  
   640x360       59.86    59.83    59.84    59.32  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.63    59.82  
   400x300       60.32    56.34  
   432x243       59.92    59.57  
   320x240       60.05  
   360x202       59.51    59.13  
   320x180       59.84    59.32  

```

[B]lsmod
[/B][/FONT][/SIZE]```
Module                  Size  Used by
rfcomm                 77824  4
ip6table_filter        16384  0
ip6_tables             28672  1 ip6table_filter
iptable_filter         16384  0
pci_stub               16384  1
vboxpci                24576  0
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               471040  3 vboxpci,vboxnetadp,vboxnetflt
ccm                    20480  6
cmac                   16384  1
bnep                   20480  2
binfmt_misc            20480  1
uvcvideo               86016  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 videobuf2_v4l2,uvcvideo
btusb                  45056  0
btrtl                  16384  1 btusb
videodev              184320  3 videobuf2_core,videobuf2_v4l2,uvcvideo
btbcm                  16384  1 btusb
btintel                16384  1 btusb
media                  40960  2 videodev,uvcvideo
bluetooth             548864  33 btrtl,btintel,btbcm,bnep,btusb,rfcomm
ecdh_generic           24576  2 bluetooth
snd_hda_codec_hdmi     49152  1
snd_hda_codec_realtek   106496  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
arc4                   16384  2
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
snd_hda_intel          40960  8
kvm_intel             212992  0
snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           81920  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
kvm                   598016  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
snd_hwdep              20480  1 snd_hda_codec
ghash_clmulni_intel    16384  0
pcbc                   16384  0
snd_pcm                98304  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
aesni_intel           188416  6
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
iwlmvm                364544  0
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
mac80211              778240  1 iwlmvm
intel_cstate           20480  0
snd_rawmidi            32768  1 snd_seq_midi
intel_rapl_perf        16384  0
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
joydev                 24576  0
iwlwifi               282624  1 iwlmvm
input_leds             16384  0
serio_raw              16384  0
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
msi_wmi                16384  0
snd_timer              32768  2 snd_seq,snd_pcm
sparse_keymap          16384  1 msi_wmi
cfg80211              622592  3 iwlmvm,iwlwifi,mac80211
rtsx_pci_ms            20480  0
mei_me                 40960  0
mei                    90112  1 mei_me
memstick               16384  1 rtsx_pci_ms
lpc_ich                24576  0
snd                    81920  27 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
shpchp                 36864  0
soundcore              16384  1 snd
intel_smartconnect     16384  0
acpi_pad              180224  0
tpm_infineon           20480  0
mac_hid                16384  0
sch_fq_codel           20480  5
nfsd                  339968  13
auth_rpcgss            61440  1 nfsd
nfs_acl                16384  1 nfsd
lockd                  90112  1 nfsd
grace                  16384  2 nfsd,lockd
parport_pc             36864  0
ppdev                  20480  0
sunrpc                335872  18 nfsd,auth_rpcgss,lockd,nfs_acl
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              28672  1 iptable_filter
x_tables               40960  4 ip6table_filter,iptable_filter,ip6_tables,ip_tables
autofs4                40960  2
btrfs                1130496  0
zstd_compress         163840  1 btrfs
raid10                 53248  0
raid456               143360  0
async_raid6_recov      20480  1 raid456
async_memcpy           16384  2 raid456,async_raid6_recov
async_pq               16384  2 raid456,async_raid6_recov
async_xor              16384  3 async_pq,raid456,async_raid6_recov
async_tx               16384  5 async_pq,async_memcpy,async_xor,raid456,async_raid6_recov
xor                    24576  2 async_xor,btrfs
raid6_pq              114688  4 async_pq,btrfs,raid456,async_raid6_recov
libcrc32c              16384  1 raid456
raid1                  40960  0
raid0                  20480  0
multipath              16384  0
linear                 16384  0
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 usbhid,hid_generic
i915                 1617920  29
rtsx_pci_sdmmc         24576  0
i2c_algo_bit           16384  1 i915
drm_kms_helper        172032  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
psmouse               147456  0
ahci                   36864  1
drm                   401408  16 drm_kms_helper,i915
libahci                32768  1 ahci
rtsx_pci               65536  2 rtsx_pci_sdmmc,rtsx_pci_ms
wmi                    24576  1 msi_wmi
video                  45056  2 msi_wmi,i915
Module                  Size  Used by
rfcomm                 77824  4
ip6table_filter        16384  0
ip6_tables             28672  1 ip6table_filter
iptable_filter         16384  0
pci_stub               16384  1
vboxpci                24576  0
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               471040  3 vboxpci,vboxnetadp,vboxnetflt
ccm                    20480  6
cmac                   16384  1
bnep                   20480  2
binfmt_misc            20480  1
uvcvideo               86016  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 videobuf2_v4l2,uvcvideo
btusb                  45056  0
btrtl                  16384  1 btusb
videodev              184320  3 videobuf2_core,videobuf2_v4l2,uvcvideo
btbcm                  16384  1 btusb
btintel                16384  1 btusb
media                  40960  2 videodev,uvcvideo
bluetooth             548864  33 btrtl,btintel,btbcm,bnep,btusb,rfcomm
ecdh_generic           24576  2 bluetooth
snd_hda_codec_hdmi     49152  1
snd_hda_codec_realtek   106496  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
arc4                   16384  2
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
snd_hda_intel          40960  8
kvm_intel             212992  0
snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           81920  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
kvm                   598016  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
snd_hwdep              20480  1 snd_hda_codec
ghash_clmulni_intel    16384  0
pcbc                   16384  0
snd_pcm                98304  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
aesni_intel           188416  6
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
iwlmvm                364544  0
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
mac80211              778240  1 iwlmvm
intel_cstate           20480  0
snd_rawmidi            32768  1 snd_seq_midi
intel_rapl_perf        16384  0
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
joydev                 24576  0
iwlwifi               282624  1 iwlmvm
input_leds             16384  0
serio_raw              16384  0
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
msi_wmi                16384  0
snd_timer              32768  2 snd_seq,snd_pcm
sparse_keymap          16384  1 msi_wmi
cfg80211              622592  3 iwlmvm,iwlwifi,mac80211
rtsx_pci_ms            20480  0
mei_me                 40960  0
mei                    90112  1 mei_me
memstick               16384  1 rtsx_pci_ms
lpc_ich                24576  0
snd                    81920  27 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
shpchp                 36864  0
soundcore              16384  1 snd
intel_smartconnect     16384  0
acpi_pad              180224  0
tpm_infineon           20480  0
mac_hid                16384  0
sch_fq_codel           20480  5
nfsd                  339968  13
auth_rpcgss            61440  1 nfsd
nfs_acl                16384  1 nfsd
lockd                  90112  1 nfsd
grace                  16384  2 nfsd,lockd
parport_pc             36864  0
ppdev                  20480  0
sunrpc                335872  18 nfsd,auth_rpcgss,lockd,nfs_acl
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              28672  1 iptable_filter
x_tables               40960  4 ip6table_filter,iptable_filter,ip6_tables,ip_tables
autofs4                40960  2
btrfs                1130496  0
zstd_compress         163840  1 btrfs
raid10                 53248  0
raid456               143360  0
async_raid6_recov      20480  1 raid456
async_memcpy           16384  2 raid456,async_raid6_recov
async_pq               16384  2 raid456,async_raid6_recov
async_xor              16384  3 async_pq,raid456,async_raid6_recov
async_tx               16384  5 async_pq,async_memcpy,async_xor,raid456,async_raid6_recov
xor                    24576  2 async_xor,btrfs
raid6_pq              114688  4 async_pq,btrfs,raid456,async_raid6_recov
libcrc32c              16384  1 raid456
raid1                  40960  0
raid0                  20480  0
multipath              16384  0
linear                 16384  0
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 usbhid,hid_generic
i915                 1617920  29
rtsx_pci_sdmmc         24576  0
i2c_algo_bit           16384  1 i915
drm_kms_helper        172032  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
psmouse               147456  0
ahci                   36864  1
drm                   401408  16 drm_kms_helper,i915
libahci                32768  1 ahci
rtsx_pci               65536  2 rtsx_pci_sdmmc,rtsx_pci_ms
wmi                    24576  1 msi_wmi
video                  45056  2 msi_wmi,i915

```


**lspci | grep -i intel**
```
[SIZE=1][FONT=arial]
[/FONT][/SIZE]00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 5500 (rev 09)
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)
00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 (rev e3)
00:1c.2 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 (rev e3)
00:1c.3 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #4 (rev e3)
00:1d.0 USB controller: Intel Corporation Wildcat Point-LP USB EHCI Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] (rev 03)
00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation Wireless 7265 (rev 61)

```

---

### Post by antnh6 on 2018-11-03
~: grep -i intel /var/log/Xorg.0.log
grep: /var/log/Xorg.0.log: No such file or directory

---

