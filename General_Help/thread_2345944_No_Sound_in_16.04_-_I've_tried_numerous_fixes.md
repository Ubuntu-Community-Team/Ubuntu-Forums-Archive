---
title: "No Sound in 16.04 - I've tried numerous fixes"
date: 2016-12-09
forum: General Help
---

### Post by elithebeatmaker on 2016-12-09
Fairly Fresh install of 16.04 on an Acer Aspire R (i5 7200u  Kabylake). Sound was working fine. After installing system updates from  Software Center and a restart sound was very quiet at maximum. After  another restart no sound at all.

I've tried uninstalling and reinstalling alsa/pulseaudio. I've done config edits, and edited speech-dispatcher. I've updated/reinstalled my kernel.
 After trying a bunch of stuff it randomly started working after one  of my restarts, but the audio was still very quiet. Alsamixer was  working, etc. Edited alsa-base from a suggestion to fix low sound, and  now I'm back to square one after a restart, no sound and only Dummy  Device in sound settings.
  
Current ouputs:

  sudo alsamixer
  [HTML]cannot open mixer: No such file or directory
[/HTML]  aplay -l
  [HTML]aplay: device_list:268: no soundcards found...
[/HTML]  sudo lspci
  [HTML]00:1f.3 Audio device: Intel Corporation Device 9d71 (rev 21)
[/HTML]  cat /proc/asound/cards
  [HTML]--- no soundcards ---
     [/HTML]

---

### Post by karl96 on 2016-12-09
Hi,

What's the output of ```
 lsmod 
```

It's possible there are two conflicting kernel modules being loaded and alsa is being dumb.

---

### Post by elithebeatmaker on 2016-12-09
I updated to 16.10 thinking it might be a kernel issue and it would fix it but it did not fix it. This is the lsmod output after upgrade:

```
Module                  Size  Used by
rfcomm                 77824  0
bnep                   20480  2
binfmt_misc            20480  1
nls_iso8859_1          16384  1
arc4                   16384  2
hid_sensor_accel_3d    16384  1
hid_sensor_trigger     16384  2 hid_sensor_accel_3d
industrialio_triggered_buffer    16384  1 hid_sensor_accel_3d
kfifo_buf              16384  1 industrialio_triggered_buffer
industrialio           65536  5 hid_sensor_accel_3d,hid_sensor_trigger,industrialio_triggered_buffer,kfifo_buf
hid_sensor_iio_common    16384  2 hid_sensor_accel_3d,hid_sensor_trigger
rtsx_usb_ms            20480  0
hid_sensor_custom      20480  0
hid_sensor_hub         20480  4 hid_sensor_accel_3d,hid_sensor_iio_common,hid_sensor_trigger,hid_sensor_custom
rtsx_usb_sdmmc         28672  0
memstick               20480  1 rtsx_usb_ms
i2c_designware_platform    16384  0
joydev                 20480  0
rtsx_usb               24576  2 rtsx_usb_sdmmc,rtsx_usb_ms
i2c_designware_core    20480  1 i2c_designware_platform
acer_wmi               20480  0
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
coretemp               16384  0
kvm_intel             188416  0
kvm                   598016  1 kvm_intel
uvcvideo               90112  0
irqbypass              16384  1 kvm
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
snd_soc_skl            65536  0
ath10k_pci             45056  0
videodev              180224  3 uvcvideo,videobuf2_core,videobuf2_v4l2
crct10dif_pclmul       16384  0
snd_soc_skl_ipc        45056  1 snd_soc_skl
ath10k_core           335872  1 ath10k_pci
media                  40960  2 uvcvideo,videodev
hid_multitouch         20480  0
snd_soc_sst_ipc        16384  1 snd_soc_skl_ipc
crc32_pclmul           16384  0
snd_soc_sst_dsp        32768  1 snd_soc_skl_ipc
ath                    32768  1 ath10k_core
snd_hda_ext_core       28672  1 snd_soc_skl
ghash_clmulni_intel    16384  0
mac80211              757760  1 ath10k_core
aesni_intel           167936  0
aes_x86_64             20480  1 aesni_intel
snd_soc_sst_match      16384  1 snd_soc_skl
lrw                    16384  1 aesni_intel
cfg80211              581632  3 mac80211,ath,ath10k_core
snd_hda_core           86016  2 snd_hda_ext_core,snd_soc_skl
glue_helper            16384  1 aesni_intel
snd_soc_core          233472  1 snd_soc_skl
btusb                  45056  0
ablk_helper            16384  1 aesni_intel
btrtl                  16384  1 btusb
cryptd                 24576  3 ablk_helper,ghash_clmulni_intel,aesni_intel
snd_compress           20480  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
input_leds             16384  0
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_pcm               110592  5 snd_pcm_dmaengine,snd_hda_ext_core,snd_hda_core,snd_soc_skl,snd_soc_core
hci_uart               94208  0
serio_raw              16384  0
snd_timer              32768  1 snd_pcm
idma64                 20480  0
btbcm                  16384  2 hci_uart,btusb
btqca                  16384  1 hci_uart
virt_dma               16384  1 idma64
ucsi                   16384  0
btintel                16384  2 hci_uart,btusb
snd                    86016  4 snd_compress,snd_timer,snd_soc_core,snd_pcm
acpi_pad               20480  0
mei_me                 40960  0
bluetooth             552960  33 btrtl,hci_uart,btintel,btqca,bnep,btbcm,rfcomm,btusb
mei                   102400  1 mei_me
intel_vbtn             16384  0
intel_lpss_acpi        16384  0
intel_lpss_pci         16384  0
intel_lpss             16384  2 intel_lpss_pci,intel_lpss_acpi
sparse_keymap          16384  2 acer_wmi,intel_vbtn
shpchp                 36864  0
soundcore              16384  1 snd
mac_hid                16384  0
intel_pch_thermal      16384  0
tpm_crb                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              28672  0
x_tables               36864  1 ip_tables
autofs4                40960  2
usbhid                 53248  0
i915                 1314816  125
i2c_algo_bit           16384  1 i915
drm_kms_helper        167936  1 i915
ahci                   36864  3
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
libahci                32768  1 ahci
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   368640  5 i915,drm_kms_helper
i2c_hid                20480  0
hid                   118784  4 hid_sensor_hub,i2c_hid,usbhid,hid_multitouch
wmi                    16384  1 acer_wmi
pinctrl_sunrisepoint    28672  0
video                  40960  2 acer_wmi,i915
pinctrl_intel          20480  1 pinctrl_sunrisepoint
fjes                   28672  0

```

---

### Post by Yellow Pasque on 2016-12-10
Run this first (just makes lspci output more human readable):
```
sudo update-pciids
```

Then, get detailed info:
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by elithebeatmaker on 2016-12-11
Here's the updated lspci output

```
00:00.0 Host bridge: Intel Corporation Device 5904 (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Device 5916 (rev 02)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #0 (rev 21)
00:15.1 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #1 (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1d.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #9 (rev f1)
00:1d.3 PCI bridge: Intel Corporation Device 9d1b (rev f1)
00:1f.0 ISA bridge: Intel Corporation Device 9d58 (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Device 9d71 (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
02:00.0 Network controller: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 32)


```

and the other requested alsa output

```
!!################################
!!ALSA Information Script v 0.4.64
!!################################

!!Script ran on: Sun Dec 11 05:13:39 UTC 2016


!!Linux Distribution
!!------------------

Ubuntu 16.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 16.10" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 16.10" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/" PRIVACY_POLICY_URL="http://www.ubuntu.com/legal/terms-and-policies/privacy-policy" UBUNTU_CODENAME=yakkety


!!DMI Information
!!---------------

Manufacturer:      Acer
Product Name:      Aspire R5-571T
Product Version:   V1.05
Firmware Version:  V1.05


!!Kernel Information
!!------------------

Kernel release:    4.8.0-30-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k4.8.0-30-generic
Library version:    1.1.2
Utilities version:  1.1.2


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

Jack:
      Installed - Yes (/usr/bin/jackd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

--- no soundcards ---


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1f.3 Audio device: Intel Corporation Device 9d71 (rev 21)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:1f.3 0403: 8086:9d71 (rev 21)
    Subsystem: 1025:112d


!!Modprobe options (Sound related)
!!--------------------------------

snd_pcsp: index=-2
snd_usb_audio: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_usb_audio: index=-2
snd_usb_caiaq: index=-2
snd_usb_ua101: index=-2
snd_usb_us122l: index=-2
snd_usb_usx2y: index=-2
snd_hda_intel: index=1
snd_cmipci: mpu_port=0x330 fm_port=0x388
snd_pcsp: index=-2
snd_usb_audio: index=-2
snd_hda_intel: model=acer-aspire-8930g


!!Loaded sound module options
!!---------------------------


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  1 Dec 10 20:28 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Dec 10 20:28 /dev/snd/timer


!!Aplay/Arecord output
!!--------------------

APLAY

aplay: device_list:268: no soundcards found...

ARECORD

arecord: device_list:268: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!--------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
ccm
cmac
rfcomm
bnep
binfmt_misc
nls_iso8859_1
hid_sensor_accel_3d
hid_sensor_trigger
industrialio_triggered_buffer
kfifo_buf
industrialio
hid_sensor_iio_common
hid_sensor_custom
hid_sensor_hub
i2c_designware_platform
joydev
i2c_designware_core
acer_wmi
arc4
rtsx_usb_ms
memstick
uvcvideo
intel_rapl
x86_pkg_temp_thermal
videobuf2_vmalloc
videobuf2_memops
coretemp
videobuf2_v4l2
videobuf2_core
kvm_intel
kvm
snd_soc_skl
videodev
snd_soc_skl_ipc
hid_multitouch
snd_soc_sst_ipc
irqbypass
snd_soc_sst_dsp
media
snd_hda_ext_core
snd_soc_sst_match
ath10k_pci
ath10k_core
snd_hda_core
snd_soc_core
snd_compress
ac97_bus
ath
snd_pcm_dmaengine
mac80211
cfg80211
crct10dif_pclmul
input_leds
idma64
crc32_pclmul
snd_pcm
hci_uart
btusb
ghash_clmulni_intel
aesni_intel
aes_x86_64
serio_raw
lrw
glue_helper
virt_dma
btrtl
btbcm
ablk_helper
cryptd
intel_lpss_acpi
ucsi
btqca
snd_timer
btintel
snd
acpi_pad
mei_me
bluetooth
mei
intel_lpss_pci
intel_lpss
intel_vbtn
shpchp
soundcore
sparse_keymap
intel_pch_thermal
mac_hid
tpm_crb
parport_pc
ppdev
lp
parport
ip_tables
x_tables
autofs4
rtsx_usb_sdmmc
rtsx_usb
usbhid
i915
i2c_algo_bit
drm_kms_helper
syscopyarea
sysfillrect
sysimgblt
fb_sys_fops
ahci
drm
libahci
i2c_hid
hid
wmi
pinctrl_sunrisepoint
video
pinctrl_intel
fjes


!!ALSA/HDA dmesg
!!--------------

[   14.125993] Linux video capture interface: v2.00
[   14.186235] snd_soc_skl 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[   14.479195] ------------[ cut here ]------------
--
[   14.479199] memremap attempted on mixed range 0x0000000000000000 size: 0x0
[   14.479199] Modules linked in: videobuf2_v4l2 videobuf2_core kvm_intel kvm snd_soc_skl( ) videodev snd_soc_skl_ipc hid_multitouch snd_soc_sst_ipc irqbypass snd_soc_sst_dsp media snd_hda_ext_core snd_soc_sst_match ath10k_pci ath10k_core snd_hda_core snd_soc_core snd_compress ac97_bus ath snd_pcm_dmaengine mac80211 cfg80211 crct10dif_pclmul input_leds idma64 crc32_pclmul snd_pcm hci_uart btusb ghash_clmulni_intel aesni_intel aes_x86_64 serio_raw lrw glue_helper virt_dma btrtl btbcm ablk_helper cryptd intel_lpss_acpi ucsi btqca snd_timer btintel snd acpi_pad mei_me bluetooth mei intel_lpss_pci intel_lpss intel_vbtn shpchp soundcore sparse_keymap intel_pch_thermal mac_hid tpm_crb parport_pc ppdev lp parport ip_tables x_tables autofs4 rtsx_usb_sdmmc rtsx_usb usbhid i915 i2c_algo_bit drm_kms_helper syscopyarea
[   14.479223]  sysfillrect sysimgblt fb_sys_fops ahci drm libahci i2c_hid hid wmi pinctrl_sunrisepoint video pinctrl_intel fjes
--
[   14.479243]  [<ffffffff9b79e284>] memremap 0xb4/0x180
[   14.479247]  [<ffffffffc0901428>] skl_nhlt_init 0x78/0xd0 [snd_soc_skl]
[   14.479249]  [<ffffffffc08ffad1>] skl_probe 0x2c1/0x7e0 [snd_soc_skl]
[   14.479251]  [<ffffffff9ba857c5>] local_pci_probe 0x45/0xa0
--
[   14.479264]  [<ffffffff9ba850fc>] __pci_register_driver 0x4c/0x50
[   14.479266]  [<ffffffffc08a601e>] skl_driver_init 0x1e/0x1000 [snd_soc_skl]
[   14.479267]  [<ffffffff9b602190>] do_one_initcall 0x50/0x190
--
[   14.479446] ------------[ cut here ]------------
[   14.479451] WARNING: CPU: 0 PID: 376 at /build/linux-JD982z/linux-4.8.0/sound/hda/hdac_i915.c:423 snd_hdac_i915_exit 0x71/0x90 [snd_hda_core]
[   14.479451] Modules linked in: videobuf2_v4l2 videobuf2_core kvm_intel kvm snd_soc_skl( ) videodev snd_soc_skl_ipc hid_multitouch snd_soc_sst_ipc irqbypass snd_soc_sst_dsp media snd_hda_ext_core snd_soc_sst_match ath10k_pci ath10k_core snd_hda_core snd_soc_core snd_compress ac97_bus ath snd_pcm_dmaengine mac80211 cfg80211 crct10dif_pclmul input_leds idma64 crc32_pclmul snd_pcm hci_uart btusb ghash_clmulni_intel aesni_intel aes_x86_64 serio_raw lrw glue_helper virt_dma btrtl btbcm ablk_helper cryptd intel_lpss_acpi ucsi btqca snd_timer btintel snd acpi_pad mei_me bluetooth mei intel_lpss_pci intel_lpss intel_vbtn shpchp soundcore sparse_keymap intel_pch_thermal mac_hid tpm_crb parport_pc ppdev lp parport ip_tables x_tables autofs4 rtsx_usb_sdmmc rtsx_usb usbhid i915 i2c_algo_bit drm_kms_helper syscopyarea
[   14.479468]  sysfillrect sysimgblt fb_sys_fops ahci drm libahci i2c_hid hid wmi pinctrl_sunrisepoint video pinctrl_intel fjes
--
[   14.479481]  [<ffffffff9b68322d>] warn_slowpath_null 0x1d/0x20
[   14.479484]  [<ffffffffc0727cc1>] snd_hdac_i915_exit 0x71/0x90 [snd_hda_core]
[   14.479494]  [<ffffffffc08ff376>] skl_free 0x76/0x80 [snd_soc_skl]
[   14.479496]  [<ffffffffc08ffcf2>] skl_probe 0x4e2/0x7e0 [snd_soc_skl]
[   14.479498]  [<ffffffff9ba857c5>] local_pci_probe 0x45/0xa0
--
[   14.479509]  [<ffffffff9ba850fc>] __pci_register_driver 0x4c/0x50
[   14.479511]  [<ffffffffc08a601e>] skl_driver_init 0x1e/0x1000 [snd_soc_skl]
[   14.479512]  [<ffffffff9b602190>] do_one_initcall 0x50/0x190



```

Note: The last line of the modeprobe options was an attempted fix that didnt work.

---

### Post by Yellow Pasque on 2016-12-11
1. Get rid of the model=acer-aspire-8930g option.

2. I don't know what to suggest except trying a 4.9.x kernel
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.9-rc8/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.9-rc8/)

---

### Post by FerryGnu on 2016-12-11
I have an Acer v5-171 and had the same problem. Could not fix, it so bought a USB sound card, about six-bucks, solved the issue. Just assign it in the Sound-Settings.

---

