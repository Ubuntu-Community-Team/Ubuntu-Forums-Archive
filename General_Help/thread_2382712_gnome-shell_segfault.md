---
title: "gnome-shell segfault"
date: 2018-01-16
forum: General Help
---

### Post by bombacha on 2018-01-16
Ubuntu 17.10 x64, the message show every time after boot.
```
[ 9292.360069] gnome-shell[6058]: segfault at 38 ip 00007fd19e355cf0 sp 00007fffdbe5e408 error 4 in libmutter-1.so.0.0.0[7fd19e303000+142000]
```
```

uname -r
4.13.0-25-generic

```
```
LANG=us.UTF8 sudo lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD9x0/RX980 Host Bridge (rev 02)
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD/ATI] RD890S/RD990 I/O Memory Management Unit (IOMMU)
00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890/RD9x0/RX980 PCI to PCI bridge (PCI Express GFX port 0)
00:09.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890/RD9x0/RX980 PCI to PCI bridge (PCI Express GPP Port 4)
00:0a.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890/RD9x0/RX980 PCI to PCI bridge (PCI Express GPP Port 5)
00:0c.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD890/RD990 PCI to PCI bridge (PCI Express GFX2 port 1)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.2 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB900 PCI to PCI bridge (PCIE port 2)
00:15.3 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB900 PCI to PCI bridge (PCIE port 3)
00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde PRO [Radeon HD 7750/8740 / R7 250E]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
02:00.0 USB controller: VIA Technologies, Inc. VL805 USB 3.0 Host Controller (rev 01)
03:00.0 SATA controller: Marvell Technology Group Ltd. 88SE9172 SATA 6Gb/s Controller (rev 12)
04:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 03)
05:04.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
08:00.0 SATA controller: Marvell Technology Group Ltd. 88SE9172 SATA 6Gb/s Controller (rev 12)
09:00.0 Multimedia video controller: Blackmagic Design Intensity Pro

```

```
LANG=us.UTF-8 sudo lshw -short|grep display
/0/100/2/0                  display     Cape Verde PRO [Radeon HD 7750/8740 / R7

```
```
lsmod
Module                  Size  Used by
st                     57344  0
lp                     20480  0
parport_pc             32768  0
binfmt_misc            20480  1
uas                    24576  0
usb_storage            69632  1 uas
nls_iso8859_1          16384  1
edac_mce_amd           28672  0
kvm_amd              2179072  0
kvm                   581632  1 kvm_amd
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
snd_virtuoso           49152  4
snd_oxygen_lib         40960  1 snd_virtuoso
pcbc                   16384  0
snd_mpu401_uart        16384  1 snd_oxygen_lib
aesni_intel           188416  0
snd_hda_codec_hdmi     49152  1
snd_hda_intel          40960  4
snd_hda_codec         126976  2 snd_hda_intel,snd_hda_codec_hdmi
snd_hda_core           81920  3 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi
snd_hwdep              20480  1 snd_hda_codec
aes_x86_64             20480  1 aesni_intel
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
snd_rawmidi            32768  2 snd_mpu401_uart,snd_seq_midi
snd_pcm                98304  5 snd_oxygen_lib,snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
hid_pl                 16384  0
joydev                 20480  0
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
ff_memless             16384  1 hid_pl
fam15h_power           16384  0
k10temp                16384  0
input_leds             16384  0
snd                    81920  28 snd_oxygen_lib,snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_hda_codec_hdmi,snd_seq_device,snd_virtuoso,snd_pcm
soundcore              16384  1 snd
i2c_piix4              24576  0
shpchp                 36864  0
mac_hid                16384  0
tpm_infineon           20480  0
ppdev                  20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  0
x_tables               40960  1 ip_tables
autofs4                40960  2
amdgpu               2007040  0
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  3 hid_generic,usbhid,hid_pl
amdkfd                188416  1
amd_iommu_v2           20480  1 amdkfd
radeon               1470464  35
mxm_wmi                16384  0
i2c_algo_bit           16384  2 amdgpu,radeon
ttm                    94208  2 amdgpu,radeon
drm_kms_helper        167936  2 amdgpu,radeon
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
r8169                  81920  0
fb_sys_fops            16384  1 drm_kms_helper
pata_acpi              16384  0
mii                    16384  1 r8169
drm                   356352  30 amdgpu,radeon,ttm,drm_kms_helper
ahci                   36864  4
pata_atiixp            16384  0
libahci                32768  1 ahci
wmi                    24576  1 mxm_wmi

```

---

