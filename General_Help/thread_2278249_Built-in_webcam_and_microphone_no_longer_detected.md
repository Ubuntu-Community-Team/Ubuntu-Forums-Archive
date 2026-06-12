---
title: "Built-in webcam and microphone no longer detected"
date: 2015-05-14
forum: General Help
---

### Post by imaginaryfruit on 2015-05-14
Hi,

I have a laptop with a built-in microphone and webcam. Both had been working fine until a couple of weeks ago; now neither Skype nor Cheese detects the webcam. When I go to Sound Settings the "internal microphone" is listed but speaking into it does not affect the orange volume indicators. (I was using 14.04 when they stopped working and I upgraded to 15.04 today.) 

I'm not sure exactly what information is useful, but here is the output of lspci:

```
:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
09:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
0b:00.0 USB controller: Texas Instruments TUSB73x0 SuperSpeed USB 3.0 xHCI Host Controller (rev 02)
:~$ 
```

and here's the output of lsmod:

```
:~$ lsmod
Module                  Size  Used by
psmouse               118784  0 
ctr                    16384  1 
ccm                    20480  1 
binfmt_misc            20480  1 
rfcomm                 69632  8 
bnep                   20480  2 
nvram                  16384  0 
msr                    16384  0 
snd_hda_codec_hdmi     53248  1 
snd_hda_codec_conexant    24576  1 
snd_hda_codec_generic    69632  1 snd_hda_codec_conexant
snd_hda_intel          32768  3 
snd_hda_controller     32768  1 snd_hda_intel
snd_hda_codec         143360  5 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
ath3k                  16384  0 
snd_hwdep              20480  1 snd_hda_codec
btusb                  32768  0 
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
bluetooth             491520  23 bnep,ath3k,btusb,rfcomm
snd_seq_midi           16384  0 
arc4                   16384  2 
ath9k                 147456  0 
dell_wmi               16384  0 
ath9k_common           32768  1 ath9k
snd_seq_midi_event     16384  1 snd_seq_midi
ath9k_hw              458752  2 ath9k_common,ath9k
snd_rawmidi            32768  1 snd_seq_midi
sparse_keymap          16384  1 dell_wmi
dell_laptop            16384  0 
intel_rapl             20480  0 
dcdbas                 16384  1 dell_laptop
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
iosf_mbi               16384  1 intel_rapl
i8k                    16384  0 
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
mac80211              720896  1 ath9k
x86_pkg_temp_thermal    16384  0 
snd_timer              32768  2 snd_pcm,snd_seq
intel_powerclamp       20480  0 
coretemp               16384  0 
cfg80211              540672  4 ath,ath9k_common,ath9k,mac80211
kvm_intel             151552  0 
kvm                   483328  1 kvm_intel
snd                    90112  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
crct10dif_pclmul       16384  0 
crc32_pclmul           16384  0 
joydev                 20480  0 
serio_raw              16384  0 
ghash_clmulni_intel    16384  0 
soundcore              16384  2 snd,snd_hda_codec
cryptd                 20480  1 ghash_clmulni_intel
shpchp                 40960  0 
mei_me                 20480  0 
lpc_ich                24576  0 
mei                    90112  1 mei_me
dell_smo8800           16384  0 
mac_hid                16384  0 
cuse                   16384  3 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
autofs4                40960  2 
ums_realtek            20480  0 
uas                    24576  0 
usb_storage            69632  2 uas,ums_realtek
i915                 1052672  3 
i2c_algo_bit           16384  1 i915
drm_kms_helper        122880  1 i915
drm                   344064  5 i915,drm_kms_helper
ahci                   36864  2 
libahci                32768  1 ahci
r8169                  81920  0 
mii                    16384  1 r8169
wmi                    20480  1 dell_wmi
video                  20480  1 i915
:~$ 
```

Any ideas how to get microphone and webcam working again?

Thanks!

---

