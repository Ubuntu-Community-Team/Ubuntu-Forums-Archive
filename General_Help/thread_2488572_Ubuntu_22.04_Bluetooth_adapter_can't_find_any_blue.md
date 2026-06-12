---
title: "Ubuntu 22.04 Bluetooth adapter can't find any bluetooth devices."
date: 2023-07-09
forum: General Help
---

### Post by jsn33 on 2023-07-09
Hello there! I am using Ubuntu 22.04 LTS on Asus Vivobook15 M1502IA, model of bluetooth adapter is rtl8852be. I have already tried things like downloading and installing drivers for my bluetooth model, but it still doesn't see any devices. If u need additional information I can post it here.

---

### Post by jeremy31 on 2023-07-09
Post results from terminal for ```
uname -r; lsusb; sudo dmesg | egrep -i 'blue|firm'
```

---

### Post by jsn33 on 2023-07-09
```
5.19.0-46-generic

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 3277:0029 Shine-optics USB2.0 HD UVC WebCam
Bus 003 Device 002: ID 13d3:3571 IMC Networks Bluetooth Radio
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

[    0.114536] Spectre V2 : Enabling Speculation Barrier for firmware calls
[    0.293475] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    0.304136] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-7f] only partially covers this bridge
[    1.500801] usb 3-2: Product: Bluetooth Radio
[    2.564422] Bluetooth: Core ver 2.22
[    2.564441] NET: Registered PF_BLUETOOTH protocol family
[    2.564442] Bluetooth: HCI device and connection manager initialized
[    2.564445] Bluetooth: HCI socket layer initialized
[    2.564447] Bluetooth: L2CAP socket layer initialized
[    2.564450] Bluetooth: SCO socket layer initialized
[    2.694476] rtw89_8852be 0000:02:00.0: Direct firmware load for rtw89/rtw8852b_fw-1.bin failed with error -2
[    2.694779] rtw89_8852be 0000:02:00.0: loaded firmware rtw89/rtw8852b_fw.bin
[    2.697286] rtw89_8852be 0000:02:00.0: Firmware version 0.27.32.1, cmd version 0, type 1
[    2.697293] rtw89_8852be 0000:02:00.0: Firmware version 0.27.32.1, cmd version 0, type 3
[    2.827805] Bluetooth: hci0: Failed to read codec capabilities (-22)
[    3.923434] [drm] Loading DMUB firmware via PSP: version=0x0101001F
[    3.929548] [drm] Found VCN firmware Version ENC: 1.16 DEC: 5 VEP: 0 Revision: 3
[    3.929603] amdgpu 0000:04:00.0: amdgpu: Will use PSP to load VCN firmware
[    3.956715] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    3.956723] Bluetooth: BNEP filters: protocol multicast
[    3.956730] Bluetooth: BNEP socket layer initialized
[    4.001860] Bluetooth: RFCOMM TTY layer initialized
[    4.001881] Bluetooth: RFCOMM socket layer initialized
[    4.001888] Bluetooth: RFCOMM ver 1.11
```

---

### Post by jeremy31 on 2023-07-09
Secure Boot needs to be disabled, check in terminal ```
mokutil --sb
```
Then ```
sudo apt install git dkms
git clone https://github.com/jeremyb31/bluetooth-5.19.git
sudo dkms add ./bluetooth-5.19
sudo dkms install btusb/4.0
```
Reboot

---

### Post by jsn33 on 2023-07-09
I can not turn on the bluetooth now.

```
[    0.110572] Spectre V2 : Enabling Speculation Barrier for firmware calls
[    0.284694] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    0.293440] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-7f] only partially covers this bridge
[    1.504157] usb 3-2: Product: Bluetooth Radio
[    2.370815] Bluetooth: Core ver 2.22
[    2.370852] NET: Registered PF_BLUETOOTH protocol family
[    2.370853] Bluetooth: HCI device and connection manager initialized
[    2.370860] Bluetooth: HCI socket layer initialized
[    2.370863] Bluetooth: L2CAP socket layer initialized
[    2.370867] Bluetooth: SCO socket layer initialized
[    2.669949] rtw89_8852be 0000:02:00.0: Direct firmware load for rtw89/rtw8852b_fw-1.bin failed with error -2
[    2.673211] rtw89_8852be 0000:02:00.0: loaded firmware rtw89/rtw8852b_fw.bin
[    2.677866] rtw89_8852be 0000:02:00.0: Firmware version 0.27.32.1, cmd version 0, type 1
[    2.677878] rtw89_8852be 0000:02:00.0: Firmware version 0.27.32.1, cmd version 0, type 3
[    3.817353] [drm] Loading DMUB firmware via PSP: version=0x0101001F
[    3.819567] [drm] Found VCN firmware Version ENC: 1.16 DEC: 5 VEP: 0 Revision: 3
[    3.819576] amdgpu 0000:04:00.0: amdgpu: Will use PSP to load VCN firmware
[    5.410610] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    5.410615] Bluetooth: BNEP filters: protocol multicast
[    5.410619] Bluetooth: BNEP socket layer initialized
```

---

### Post by jeremy31 on 2023-07-09
```
sudo dkms uninstall btusb/4.0
sudo dkms remove btusb/4.0 --all
```
Reboot
I did find some posts on archlinux that claims this device works with the 6.4 kernel

---

### Post by jsn33 on 2023-07-09
When I was using Ubuntu 23.04 I updated my kernel version to the last and that worked, but my bluetooth connection was discontinuously.

---

### Post by jeremy31 on 2023-07-09
Lets see if this change helps ```
sudo rm -r /usr/src/btusb-4.0
cd bluetooth-5.19
git pull
sudo dkms add .
sudo dkms install btusb/4.0
```
Reboot

---

### Post by jsn33 on 2023-07-09
I can turn on it, but it still can't find any devices.

---

### Post by jeremy31 on 2023-07-09
See results for ```
sudo dmesg | egrep -i 'blue|firm'
```
We might need firmware

---

### Post by jsn33 on 2023-07-09
```
[    0.110868] Spectre V2 : Enabling Speculation Barrier for firmware calls
[    0.286644] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    0.297870] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-7f] only partially covers this bridge
[    1.512184] usb 3-2: Product: Bluetooth Radio
[    2.404349] Bluetooth: Core ver 2.22
[    2.404407] NET: Registered PF_BLUETOOTH protocol family
[    2.404409] Bluetooth: HCI device and connection manager initialized
[    2.404417] Bluetooth: HCI socket layer initialized
[    2.404420] Bluetooth: L2CAP socket layer initialized
[    2.404426] Bluetooth: SCO socket layer initialized
[    2.566934] rtw89_8852be 0000:02:00.0: Direct firmware load for rtw89/rtw8852b_fw-1.bin failed with error -2
[    2.569296] rtw89_8852be 0000:02:00.0: loaded firmware rtw89/rtw8852b_fw.bin
[    2.572141] rtw89_8852be 0000:02:00.0: Firmware version 0.27.32.1, cmd version 0, type 1
[    2.572148] rtw89_8852be 0000:02:00.0: Firmware version 0.27.32.1, cmd version 0, type 3
[    2.603405] Bluetooth: hci0: Failed to read codec capabilities (-22)
[    3.836848] [drm] Loading DMUB firmware via PSP: version=0x0101001F
[    3.840016] [drm] Found VCN firmware Version ENC: 1.16 DEC: 5 VEP: 0 Revision: 3
[    3.840029] amdgpu 0000:04:00.0: amdgpu: Will use PSP to load VCN firmware
[    3.894268] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    3.894272] Bluetooth: BNEP filters: protocol multicast
[    3.894276] Bluetooth: BNEP socket layer initialized
[    3.936152] Bluetooth: RFCOMM TTY layer initialized
[    3.936158] Bluetooth: RFCOMM socket layer initialized
[    3.936164] Bluetooth: RFCOMM ver 1.11
[   88.628707] Bluetooth: hci0: Failed to read codec capabilities (-22)
[  175.556125] Modules linked in: ccm rfcomm cmac algif_hash algif_skcipher af_alg bnep amdgpu snd_hda_codec_realtek snd_hda_codec_generic ledtrig_audio intel_rapl_msr snd_hda_codec_hdmi joydev intel_rapl_common snd_hda_intel snd_sof_amd_renoir edac_mce_amd snd_intel_dspcfg rtw_8852be(OE) snd_sof_amd_acp snd_intel_sdw_acpi rtw_8852b(OE) snd_sof_pci snd_hda_codec iommu_v2 rtw89pci(OE) snd_sof kvm_amd gpu_sched snd_hda_core rtw89core(OE) snd_sof_utils binfmt_misc snd_hwdep uvcvideo kvm drm_ttm_helper snd_soc_core videobuf2_vmalloc snd_compress btusb(OE) ttm ac97_bus videobuf2_memops btrtl(OE) mac80211 snd_pcm_dmaengine snd_seq_midi drm_display_helper snd_seq_midi_event videobuf2_v4l2 crct10dif_pclmul snd_pci_ps btbcm(OE) ghash_clmulni_intel videobuf2_common input_leds cec btintel(OE) snd_acp_pci aesni_intel snd_rawmidi snd_pci_acp6x crypto_simd rc_core videodev btmtk nls_iso8859_1 cryptd bluetooth rapl snd_pcm snd_seq drm_kms_helper serio_raw mc hid_multitouch asus_nb_wmi snd_seq_device
```

---

### Post by jsn33 on 2023-07-09
```
[    0.111037] Spectre V2 : Enabling Speculation Barrier for firmware calls
[    0.289665] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    0.300277] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-7f] only partially covers this bridge
[    1.497994] usb 3-2: Product: Bluetooth Radio
[    2.478811] Bluetooth: Core ver 2.22
[    2.478833] NET: Registered PF_BLUETOOTH protocol family
[    2.478834] Bluetooth: HCI device and connection manager initialized
[    2.478838] Bluetooth: HCI socket layer initialized
[    2.478840] Bluetooth: L2CAP socket layer initialized
[    2.478845] Bluetooth: SCO socket layer initialized
[    2.640482] rtw89_8852be 0000:02:00.0: Direct firmware load for rtw89/rtw8852b_fw-1.bin failed with error -2
[    2.640848] rtw89_8852be 0000:02:00.0: loaded firmware rtw89/rtw8852b_fw.bin
[    2.643340] rtw89_8852be 0000:02:00.0: Firmware version 0.27.32.1, cmd version 0, type 1
[    2.643344] rtw89_8852be 0000:02:00.0: Firmware version 0.27.32.1, cmd version 0, type 3
[    2.658726] Bluetooth: hci0: Failed to read codec capabilities (-22)
[    3.947896] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    3.947902] Bluetooth: BNEP filters: protocol multicast
[    3.947908] Bluetooth: BNEP socket layer initialized
[    3.973878] [drm] Loading DMUB firmware via PSP: version=0x0101001F
[    3.978516] [drm] Found VCN firmware Version ENC: 1.16 DEC: 5 VEP: 0 Revision: 3
[    3.978552] amdgpu 0000:04:00.0: amdgpu: Will use PSP to load VCN firmware
[    3.989482] Bluetooth: RFCOMM TTY layer initialized
[    3.989500] Bluetooth: RFCOMM socket layer initialized
[    3.989508] Bluetooth: RFCOMM ver 1.11
```

---

### Post by jeremy31 on 2023-07-09
What result for ```
modinfo btrtl; dkms status
```

---

### Post by jsn33 on 2023-07-09
```
[    0.111037] Spectre V2 : Enabling Speculation Barrier for firmware calls
[    0.289665] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    0.300277] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-7f] only partially covers this bridge
[    1.497994] usb 3-2: Product: Bluetooth Radio
[    2.478811] Bluetooth: Core ver 2.22
[    2.478833] NET: Registered PF_BLUETOOTH protocol family
[    2.478834] Bluetooth: HCI device and connection manager initialized
[    2.478838] Bluetooth: HCI socket layer initialized
[    2.478840] Bluetooth: L2CAP socket layer initialized
[    2.478845] Bluetooth: SCO socket layer initialized
[    2.640482] rtw89_8852be 0000:02:00.0: Direct firmware load for rtw89/rtw8852b_fw-1.bin failed with error -2
[    2.640848] rtw89_8852be 0000:02:00.0: loaded firmware rtw89/rtw8852b_fw.bin
[    2.643340] rtw89_8852be 0000:02:00.0: Firmware version 0.27.32.1, cmd version 0, type 1
[    2.643344] rtw89_8852be 0000:02:00.0: Firmware version 0.27.32.1, cmd version 0, type 3
[    2.658726] Bluetooth: hci0: Failed to read codec capabilities (-22)
[    3.947896] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    3.947902] Bluetooth: BNEP filters: protocol multicast
[    3.947908] Bluetooth: BNEP socket layer initialized
[    3.973878] [drm] Loading DMUB firmware via PSP: version=0x0101001F
[    3.978516] [drm] Found VCN firmware Version ENC: 1.16 DEC: 5 VEP: 0 Revision: 3
[    3.978552] amdgpu 0000:04:00.0: amdgpu: Will use PSP to load VCN firmware
[    3.989482] Bluetooth: RFCOMM TTY layer initialized
[    3.989500] Bluetooth: RFCOMM socket layer initialized
[    3.989508] Bluetooth: RFCOMM ver 1.11
[  257.555114] Modules linked in: ccm rfcomm cmac algif_hash algif_skcipher af_alg bnep snd_hda_codec_realtek snd_sof_amd_renoir snd_hda_codec_generic joydev amdgpu ledtrig_audio snd_hda_codec_hdmi snd_sof_amd_acp snd_sof_pci rtw_8852be(OE) intel_rapl_msr rtw_8852b(OE) snd_hda_intel snd_sof intel_rapl_common snd_intel_dspcfg snd_intel_sdw_acpi snd_sof_utils edac_mce_amd snd_hda_codec rtw89pci(OE) snd_soc_core snd_hda_core rtw89core(OE) uvcvideo iommu_v2 snd_compress snd_hwdep kvm_amd gpu_sched videobuf2_vmalloc ac97_bus snd_pcm_dmaengine drm_ttm_helper binfmt_misc videobuf2_memops snd_seq_midi kvm snd_pci_ps ttm snd_seq_midi_event snd_acp_pci videobuf2_v4l2 crct10dif_pclmul mac80211 btusb(OE) ghash_clmulni_intel snd_pci_acp6x videobuf2_common drm_display_helper snd_rawmidi btrtl(OE) btbcm(OE) aesni_intel snd_pcm cec btintel(OE) videodev crypto_simd snd_seq rc_core cryptd btmtk nls_iso8859_1 drm_kms_helper snd_pci_acp5x snd_seq_device bluetooth mc rapl input_leds snd_timer i2c_algo_bit
```

---

### Post by jsn33 on 2023-07-09
```
filename:       /lib/modules/5.19.0-46-generic/kernel/drivers/bluetooth/btrtl.ko
firmware:       rtl_bt/rtl8852bu_config.bin
firmware:       rtl_bt/rtl8852bu_fw.bin
firmware:       rtl_bt/rtl8852au_config.bin
firmware:       rtl_bt/rtl8852au_fw.bin
firmware:       rtl_bt/rtl8822b_config.bin
firmware:       rtl_bt/rtl8822b_fw.bin
firmware:       rtl_bt/rtl8821a_config.bin
firmware:       rtl_bt/rtl8821a_fw.bin
firmware:       rtl_bt/rtl8761a_config.bin
firmware:       rtl_bt/rtl8761a_fw.bin
firmware:       rtl_bt/rtl8723ds_config.bin
firmware:       rtl_bt/rtl8723ds_fw.bin
firmware:       rtl_bt/rtl8723bs_config.bin
firmware:       rtl_bt/rtl8723bs_fw.bin
firmware:       rtl_bt/rtl8723b_config.bin
firmware:       rtl_bt/rtl8723b_fw.bin
firmware:       rtl_bt/rtl8723a_fw.bin
license:        GPL
version:        0.1
description:    Bluetooth support for Realtek devices ver 0.1
author:         Daniel Drake <drake@endlessm.com>
srcversion:     056848070A5727DC2CB7494
depends:        bluetooth
retpoline:      Y
name:           btrtl
vermagic:       5.19.0-46-generic SMP preempt mod_unload modversions 
btusb/4.0: added
```

---

### Post by jeremy31 on 2023-07-09
```
sudo dkms uninstall btusb/4.0
sudo dkms remove btusb/4.0 --all
sudo rm -r /usr/src/btusb-4.0
cd bluetooth-5.19
git pull
sudo dkms add .
sudo dkms install btusb/4.0
```
Reboot
And post results for ```
modinfo btrtl; dkms status; sudo dmesg | egrep -i 'blue|firm'
```

---

### Post by jsn33 on 2023-07-09
```
filename:       /lib/modules/5.19.0-46-generic/kernel/drivers/bluetooth/btrtl.ko
firmware:       rtl_bt/rtl8852bu_config.bin
firmware:       rtl_bt/rtl8852bu_fw.bin
firmware:       rtl_bt/rtl8852au_config.bin
firmware:       rtl_bt/rtl8852au_fw.bin
firmware:       rtl_bt/rtl8822b_config.bin
firmware:       rtl_bt/rtl8822b_fw.bin
firmware:       rtl_bt/rtl8821a_config.bin
firmware:       rtl_bt/rtl8821a_fw.bin
firmware:       rtl_bt/rtl8761a_config.bin
firmware:       rtl_bt/rtl8761a_fw.bin
firmware:       rtl_bt/rtl8723ds_config.bin
firmware:       rtl_bt/rtl8723ds_fw.bin
firmware:       rtl_bt/rtl8723bs_config.bin
firmware:       rtl_bt/rtl8723bs_fw.bin
firmware:       rtl_bt/rtl8723b_config.bin
firmware:       rtl_bt/rtl8723b_fw.bin
firmware:       rtl_bt/rtl8723a_fw.bin
license:        GPL
version:        0.1
description:    Bluetooth support for Realtek devices ver 0.1
author:         Daniel Drake <drake@endlessm.com>
srcversion:     056848070A5727DC2CB7494
depends:        bluetooth
retpoline:      Y
name:           btrtl
vermagic:       5.19.0-46-generic SMP preempt mod_unload modversions 
btusb/4.0: added

[    0.110622] Spectre V2 : Enabling Speculation Barrier for firmware calls
[    0.285159] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    0.295457] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-7f] only partially covers this bridge
[    1.484569] usb 3-2: Product: Bluetooth Radio
[    2.383186] Bluetooth: Core ver 2.22
[    2.383214] NET: Registered PF_BLUETOOTH protocol family
[    2.383216] Bluetooth: HCI device and connection manager initialized
[    2.383221] Bluetooth: HCI socket layer initialized
[    2.383224] Bluetooth: L2CAP socket layer initialized
[    2.383229] Bluetooth: SCO socket layer initialized
[    2.545262] rtw89_8852be 0000:02:00.0: Direct firmware load for rtw89/rtw8852b_fw-1.bin failed with error -2
[    2.545739] rtw89_8852be 0000:02:00.0: loaded firmware rtw89/rtw8852b_fw.bin
[    2.548664] rtw89_8852be 0000:02:00.0: Firmware version 0.27.32.1, cmd version 0, type 1
[    2.548670] rtw89_8852be 0000:02:00.0: Firmware version 0.27.32.1, cmd version 0, type 3
[    2.607478] Bluetooth: hci0: Failed to read codec capabilities (-22)
[    3.720215] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    3.720221] Bluetooth: BNEP filters: protocol multicast
[    3.720225] Bluetooth: BNEP socket layer initialized
[    3.738155] [drm] Loading DMUB firmware via PSP: version=0x0101001F
[    3.741945] [drm] Found VCN firmware Version ENC: 1.16 DEC: 5 VEP: 0 Revision: 3
[    3.741963] amdgpu 0000:04:00.0: amdgpu: Will use PSP to load VCN firmware
[    3.760118] Bluetooth: RFCOMM TTY layer initialized
[    3.760134] Bluetooth: RFCOMM socket layer initialized
[    3.760142] Bluetooth: RFCOMM ver 1.11
```

---

### Post by jeremy31 on 2023-07-09
Have you rebooted?  That is not my version of btrtl and it isn't the one that came with the kernel

---

### Post by jsn33 on 2023-07-09
Yes, I have.

---

### Post by jeremy31 on 2023-07-09
Try ```
sudo dkms install btusb/4.0
```
Reboot

---

### Post by jsn33 on 2023-07-09
Kernel preparation unnecessary for this kernel. Skipping...

Building module:
cleaning build area...
'make' all KVER=5.19.0-46-generic...(bad exit status: 2)
ERROR (dkms apport): binary package for btusb: 4.0 not found
Error! Bad return status for module build on kernel: 5.19.0-46-generic (x86_64)
Consult /var/lib/dkms/btusb/4.0/build/make.log for more information.

---

### Post by jeremy31 on 2023-07-09
Try a different way
```
cd
cd bluetooth-5.19
make -C /lib/modules/$(uname -r)/build M=$(pwd) clean
make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
sudo cp btusb.ko /lib/modules/5.19.0-46-generic/kernel/drivers/bluetooth/btusb.ko
sudo cp btrtl.ko /lib/modules/5.19.0-46-generic/kernel/drivers/bluetooth/btrtl.ko
sudo depmod -a
```
Reboot

---

### Post by jsn33 on 2023-07-09
make: Entering directory '/usr/src/linux-headers-5.19.0-46-generic'
warning: the compiler differs from the one used to build the kernel 
 The kernel was built by: x86_64-linux-gnu-gcc (Ubuntu 11.3.0-1ubuntu1~22.04.1) 11.3.0
  You are using:           gcc (Ubuntu 11.3.0-1ubuntu1~22.04.1) 11.3.0
  CC [M]  /home/jsn33/bluetooth-5.19/btrtl.o
/home/jsn33/bluetooth-5.19/btrtl.c: In function &#8216;btrtl_set_quirks&#8217;:
/home/jsn33/bluetooth-5.19/btrtl.c:792:14: error: &#8216;CHIP_ID_8851B&#8217; undeclared (first use in this function); did you mean &#8216;CHIP_ID_8852B&#8217;?
  792 |         case CHIP_ID_8851B:
      |              ^~~~~~~~~~~~~
      |              CHIP_ID_8852B
/home/jsn33/bluetooth-5.19/btrtl.c:792:14: note: each undeclared identifier is reported only once for each function it appears in
make[1]: *** [scripts/Makefile.build:257: /home/jsn33/bluetooth-5.19/btrtl.o] Error 1
make: *** [Makefile:1857: /home/jsn33/bluetooth-5.19] Error 2
make: Leaving directory '/usr/src/linux-headers-5.19.0-46-generic'

---

### Post by jeremy31 on 2023-07-09
Ok, ```
cd
cd bluetooth-5.19
git pull
make -C /lib/modules/$(uname -r)/build M=$(pwd) clean
make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
sudo cp btusb.ko /lib/modules/5.19.0-46-generic/kernel/drivers/bluetooth/btusb.ko
sudo cp btrtl.ko /lib/modules/5.19.0-46-generic/kernel/drivers/bluetooth/btrtl.ko
sudo depmod -a
```
Hopefully the error is gone

---

### Post by jsn33 on 2023-07-09
Yeah, error is gone, but bluetooth doesn't turn on.

```
filename:       /lib/modules/5.19.0-46-generic/kernel/drivers/bluetooth/btrtl.ko
firmware:       rtl_bt/rtl8851bu_config.bin
firmware:       rtl_bt/rtl8851bu_fw.bin
firmware:       rtl_bt/rtl8852cu_config.bin
firmware:       rtl_bt/rtl8852cu_fw.bin
firmware:       rtl_bt/rtl8852bu_config.bin
firmware:       rtl_bt/rtl8852bu_fw.bin
firmware:       rtl_bt/rtl8852au_config.bin
firmware:       rtl_bt/rtl8852au_fw.bin
firmware:       rtl_bt/rtl8822b_config.bin
firmware:       rtl_bt/rtl8822b_fw.bin
firmware:       rtl_bt/rtl8821a_config.bin
firmware:       rtl_bt/rtl8821a_fw.bin
firmware:       rtl_bt/rtl8761a_config.bin
firmware:       rtl_bt/rtl8761a_fw.bin
firmware:       rtl_bt/rtl8723ds_config.bin
firmware:       rtl_bt/rtl8723ds_fw.bin
firmware:       rtl_bt/rtl8723bs_config.bin
firmware:       rtl_bt/rtl8723bs_fw.bin
firmware:       rtl_bt/rtl8723b_config.bin
firmware:       rtl_bt/rtl8723b_fw.bin
firmware:       rtl_bt/rtl8723a_fw.bin
license:        GPL
version:        0.2
description:    Bluetooth support for Realtek devices ver 0.2
author:         Daniel Drake <drake@endlessm.com>
srcversion:     29AA50B8988F8890D11301C
depends:        bluetooth
retpoline:      Y
name:           btrtl
vermagic:       5.19.0-46-generic SMP preempt mod_unload modversions 
btusb/4.0: added
[    0.112619] Spectre V2 : Enabling Speculation Barrier for firmware calls
[    0.287919] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    0.298259] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-7f] only partially covers this bridge
[    1.522045] usb 3-2: Product: Bluetooth Radio
[    2.396020] Bluetooth: Core ver 2.22
[    2.396063] NET: Registered PF_BLUETOOTH protocol family
[    2.396065] Bluetooth: HCI device and connection manager initialized
[    2.396072] Bluetooth: HCI socket layer initialized
[    2.396075] Bluetooth: L2CAP socket layer initialized
[    2.396079] Bluetooth: SCO socket layer initialized
[    2.609247] rtw89_8852be 0000:02:00.0: Direct firmware load for rtw89/rtw8852b_fw-1.bin failed with error -2
[    2.609860] rtw89_8852be 0000:02:00.0: loaded firmware rtw89/rtw8852b_fw.bin
[    2.612665] rtw89_8852be 0000:02:00.0: Firmware version 0.27.32.1, cmd version 0, type 1
[    2.612673] rtw89_8852be 0000:02:00.0: Firmware version 0.27.32.1, cmd version 0, type 3
[    3.901331] [drm] Loading DMUB firmware via PSP: version=0x0101001F
[    3.903560] [drm] Found VCN firmware Version ENC: 1.16 DEC: 5 VEP: 0 Revision: 3
[    3.903568] amdgpu 0000:04:00.0: amdgpu: Will use PSP to load VCN firmware
[    5.483401] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    5.483405] Bluetooth: BNEP filters: protocol multicast
[    5.483408] Bluetooth: BNEP socket layer initialized
```

---

### Post by jeremy31 on 2023-07-09
```
sudo dkms uninstall btusb/4.0
sudo dkms remove btusb/4.0 --all
sudo rm -r /usr/src/btusb-4.0
cd
rm -rf bluetooth-5.19
git clone https://github.com/jeremyb31/bluetooth-5.19.git
sudo dkms add ./bluetooth-5.19
sudo dkms install btusb/4.0
```
Post any errors if they exist, if not, reboot

---

### Post by jsn33 on 2023-07-09
Error! The module btusb 4.0 is not currently installed.
This module is not currently ACTIVE for kernel 5.19.0-46-generic (x86_64).

Only this one.

---

### Post by jeremy31 on 2023-07-09
Keep going then

---

### Post by jsn33 on 2023-07-09
Can't turn on the bluetooth.

---

### Post by jeremy31 on 2023-07-09
What result for ```
modinfo btrtl; dkms status; sudo dmesg | egrep -i 'blue|firm'
```

---

### Post by jsn33 on 2023-07-09
```
filename:       /lib/modules/5.19.0-46-generic/kernel/drivers/bluetooth/btrtl.ko
firmware:       rtl_bt/rtl8851bu_config.bin
firmware:       rtl_bt/rtl8851bu_fw.bin
firmware:       rtl_bt/rtl8852cu_config.bin
firmware:       rtl_bt/rtl8852cu_fw.bin
firmware:       rtl_bt/rtl8852bu_config.bin
firmware:       rtl_bt/rtl8852bu_fw.bin
firmware:       rtl_bt/rtl8852au_config.bin
firmware:       rtl_bt/rtl8852au_fw.bin
firmware:       rtl_bt/rtl8822b_config.bin
firmware:       rtl_bt/rtl8822b_fw.bin
firmware:       rtl_bt/rtl8821a_config.bin
firmware:       rtl_bt/rtl8821a_fw.bin
firmware:       rtl_bt/rtl8761a_config.bin
firmware:       rtl_bt/rtl8761a_fw.bin
firmware:       rtl_bt/rtl8723ds_config.bin
firmware:       rtl_bt/rtl8723ds_fw.bin
firmware:       rtl_bt/rtl8723bs_config.bin
firmware:       rtl_bt/rtl8723bs_fw.bin
firmware:       rtl_bt/rtl8723b_config.bin
firmware:       rtl_bt/rtl8723b_fw.bin
firmware:       rtl_bt/rtl8723a_fw.bin
license:        GPL
version:        0.2
description:    Bluetooth support for Realtek devices ver 0.2
author:         Daniel Drake <drake@endlessm.com>
srcversion:     29AA50B8988F8890D11301C
depends:        bluetooth
retpoline:      Y
name:           btrtl
vermagic:       5.19.0-46-generic SMP preempt mod_unload modversions 
btusb/4.0, 5.19.0-46-generic, x86_64: installed (WARNING! Diff between built and installed module!) (WARNING! Diff between built and installed module!)
[    0.111353] Spectre V2 : Enabling Speculation Barrier for firmware calls
[    0.285832] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    0.296369] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-7f] only partially covers this bridge
[    1.501020] usb 3-2: Product: Bluetooth Radio
[    2.365814] Bluetooth: Core ver 2.22
[    2.365854] NET: Registered PF_BLUETOOTH protocol family
[    2.365858] Bluetooth: HCI device and connection manager initialized
[    2.365869] Bluetooth: HCI socket layer initialized
[    2.365874] Bluetooth: L2CAP socket layer initialized
[    2.365882] Bluetooth: SCO socket layer initialized
[    2.675443] rtw89_8852be 0000:02:00.0: Direct firmware load for rtw89/rtw8852b_fw-1.bin failed with error -2
[    2.676433] rtw89_8852be 0000:02:00.0: loaded firmware rtw89/rtw8852b_fw.bin
[    2.680801] rtw89_8852be 0000:02:00.0: Firmware version 0.27.32.1, cmd version 0, type 1
[    2.680858] rtw89_8852be 0000:02:00.0: Firmware version 0.27.32.1, cmd version 0, type 3
[    3.970289] [drm] Loading DMUB firmware via PSP: version=0x0101001F
[    3.972685] [drm] Found VCN firmware Version ENC: 1.16 DEC: 5 VEP: 0 Revision: 3
[    3.972692] amdgpu 0000:04:00.0: amdgpu: Will use PSP to load VCN firmware
[    5.563831] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    5.563836] Bluetooth: BNEP filters: protocol multicast
[    5.563840] Bluetooth: BNEP socket layer initialized
```

---

### Post by jeremy31 on 2023-07-09
How about ```
modinfo btusb
```

---

### Post by jsn33 on 2023-07-09
```
filename:       /lib/modules/5.19.0-46-generic/kernel/drivers/bluetooth/btusb.ko
license:        GPL
version:        0.9
description:    Generic Bluetooth USB driver ver 0.9
author:         Marcel Holtmann <marcel@holtmann.org>
srcversion:     E76E61960D793C9314FB979
alias:          usb:v8087p0A5Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v413Cp*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v13D3p*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v050Dp*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v0B05p*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v0A5Cp*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v04CAp*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v0489p*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v0BB4p*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v105Bp*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v19FFp0239d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C10p0000d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDBp1002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v044Ep3002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v044Ep3001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BFp030Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v057Cp3800d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp8281d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp821Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp821Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp821Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp8218d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp8215d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp8213d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0A5Cp21E1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E8Dp763Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05ACp*d*dc*dsc*dp*icFFisc01ip01in*
alias:          usb:v*p*d*dc*dsc*dp*icE0isc01ip01in*
alias:          usb:v*p*d*dcE0dsc01dp04ic*isc*ip*in*
alias:          usb:v*p*d*dcE0dsc01dp01ic*isc*ip*in*
alias:          of:N*T*Cusb4ca,301aC*
alias:          of:N*T*Cusb4ca,301a
alias:          of:N*T*Cusbcf3,e300C*
alias:          of:N*T*Cusbcf3,e300
alias:          of:N*T*Cusb1286,204eC*
alias:          of:N*T*Cusb1286,204e
depends:        bluetooth,btintel,btmtk,btbcm,btrtl
retpoline:      Y
name:           btusb
vermagic:       5.19.0-46-generic SMP preempt mod_unload modversions 
parm:           disable_scofix:Disable fixup of wrong SCO buffer size (bool)
parm:           force_scofix:Force fixup of wrong SCO buffers size (bool)
parm:           enable_autosuspend:Enable USB autosuspend by default (bool)
parm:           reset:Send HCI reset command on initialization (bool)
```

---

### Post by jeremy31 on 2023-07-09
Results for ```
sudo cat /sys/kernel/debug/usb/devices | awk '/3571/' RS= 
```

---

### Post by jsn33 on 2023-07-09
```
sudo cat /sys/kernel/debug/usb/devices | awk '/3571/' RS=
T:  Bus=03 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=12   MxCh= 0
D:  Ver= 1.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=13d3 ProdID=3571 Rev= 0.00
S:  Manufacturer=Realtek
S:  Product=Bluetooth Radio
S:  SerialNumber=00e04c000001
C:* #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=500mA
I:* If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=  16 Ivl=1ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
I:* If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=(none)
E:  Ad=03(O) Atr=01(Isoc) MxPS=   0 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=   0 Ivl=1ms
I:  If#= 1 Alt= 1 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=(none)
E:  Ad=03(O) Atr=01(Isoc) MxPS=   9 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=   9 Ivl=1ms
I:  If#= 1 Alt= 2 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=(none)
E:  Ad=03(O) Atr=01(Isoc) MxPS=  17 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  17 Ivl=1ms
I:  If#= 1 Alt= 3 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=(none)
E:  Ad=03(O) Atr=01(Isoc) MxPS=  25 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  25 Ivl=1ms
I:  If#= 1 Alt= 4 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=(none)
E:  Ad=03(O) Atr=01(Isoc) MxPS=  33 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  33 Ivl=1ms
I:  If#= 1 Alt= 5 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=(none)
E:  Ad=03(O) Atr=01(Isoc) MxPS=  49 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  49 Ivl=1ms
```

---

### Post by jeremy31 on 2023-07-09
Try ```
sudo depmod -a
```
Reboot

---

### Post by jsn33 on 2023-07-09
Still not working.

---

### Post by jeremy31 on 2023-07-09
Lets try resetting back to original
```
sudo dkms uninstall btusb/4.0
sudo dkms remove btusb/4.0 --all
sudo rm -r /usr/src/btusb-4.0
rm -rf bluetooth-5.19
sudo apt install --reinstall linux-modules-extra-$(uname -r)
```
Reboot and post results for ```
dkms status; sudo cat /sys/kernel/debug/usb/devices | awk '/3571/' RS=; modinfo btrtl
```

---

### Post by jsn33 on 2023-07-09
```
T:  Bus=03 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=12   MxCh= 0
D:  Ver= 1.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=13d3 ProdID=3571 Rev= 0.00
S:  Manufacturer=Realtek
S:  Product=Bluetooth Radio
S:  SerialNumber=00e04c000001
C:* #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=500mA
I:* If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=81(I) Atr=03(Int.) MxPS=  16 Ivl=1ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
I:* If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=03(O) Atr=01(Isoc) MxPS=   0 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=   0 Ivl=1ms
I:  If#= 1 Alt= 1 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=03(O) Atr=01(Isoc) MxPS=   9 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=   9 Ivl=1ms
I:  If#= 1 Alt= 2 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=03(O) Atr=01(Isoc) MxPS=  17 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  17 Ivl=1ms
I:  If#= 1 Alt= 3 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=03(O) Atr=01(Isoc) MxPS=  25 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  25 Ivl=1ms
I:  If#= 1 Alt= 4 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=03(O) Atr=01(Isoc) MxPS=  33 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  33 Ivl=1ms
I:  If#= 1 Alt= 5 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=03(O) Atr=01(Isoc) MxPS=  49 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  49 Ivl=1ms
filename:       /lib/modules/5.19.0-46-generic/kernel/drivers/bluetooth/btrtl.ko
firmware:       rtl_bt/rtl8852cu_config.bin
firmware:       rtl_bt/rtl8852cu_fw.bin
firmware:       rtl_bt/rtl8852bu_config.bin
firmware:       rtl_bt/rtl8852bu_fw.bin
firmware:       rtl_bt/rtl8852au_config.bin
firmware:       rtl_bt/rtl8852au_fw.bin
firmware:       rtl_bt/rtl8822b_config.bin
firmware:       rtl_bt/rtl8822b_fw.bin
firmware:       rtl_bt/rtl8821a_config.bin
firmware:       rtl_bt/rtl8821a_fw.bin
firmware:       rtl_bt/rtl8761a_config.bin
firmware:       rtl_bt/rtl8761a_fw.bin
firmware:       rtl_bt/rtl8723ds_config.bin
firmware:       rtl_bt/rtl8723ds_fw.bin
firmware:       rtl_bt/rtl8723bs_config.bin
firmware:       rtl_bt/rtl8723bs_fw.bin
firmware:       rtl_bt/rtl8723b_config.bin
firmware:       rtl_bt/rtl8723b_fw.bin
firmware:       rtl_bt/rtl8723a_fw.bin
license:        GPL
version:        0.1
description:    Bluetooth support for Realtek devices ver 0.1
author:         Daniel Drake <drake@endlessm.com>
srcversion:     9F5808F54251CD9A089F889
depends:        bluetooth
retpoline:      Y
intree:         Y
name:           btrtl
vermagic:       5.19.0-46-generic SMP preempt mod_unload modversions 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        44:EF:F0:C0:8E:63:D4:C9:5C:0E:2F:E9:9E:51:FB:0F:9D:F3:DA:9A
sig_hashalgo:   sha512
signature:
```

---

### Post by jeremy31 on 2023-07-09
You could try installing the newest mainline kernel, download 
[https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.4.2/amd64/linux-headers-6.4.2-060402-generic_6.4.2-060402.202307070731_amd64.deb](https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.4.2/amd64/linux-headers-6.4.2-060402-generic_6.4.2-060402.202307070731_amd64.deb)
[https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.4.2/amd64/linux-headers-6.4.2-060402_6.4.2-060402.202307070731_all.deb](https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.4.2/amd64/linux-headers-6.4.2-060402_6.4.2-060402.202307070731_all.deb)
[https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.4.2/amd64/linux-image-unsigned-6.4.2-060402-generic_6.4.2-060402.202307070731_amd64.deb](https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.4.2/amd64/linux-image-unsigned-6.4.2-060402-generic_6.4.2-060402.202307070731_amd64.deb)
[https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.4.2/amd64/linux-modules-6.4.2-060402-generic_6.4.2-060402.202307070731_amd64.deb](https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.4.2/amd64/linux-modules-6.4.2-060402-generic_6.4.2-060402.202307070731_amd64.deb)
Then go into your Downloads directory and right click and choose "open in terminal"```
sudo dpkg -i linux-*.deb
```
Hopefully it figures out the correct install order and reboot when finished

---

### Post by jsn33 on 2023-07-10
Yeah, it helped. Now my laptop can see bluetooth devices, but my bluetooth headset doesn't play any sounds.

---

### Post by jeremy31 on 2023-07-10
Results for ```
pactl list short |grep blue
```

---

### Post by jsn33 on 2023-07-10
```
10    module-bluetooth-policy        
11    module-bluetooth-discover        
12    module-bluez5-discover
```

---

### Post by jeremy31 on 2023-07-10
That looks correct, check the sound settings and see if the speakers are listed as an output device using A2DP

---

### Post by jsn33 on 2023-07-10
Oh.. It works!!! Thanks for your help!

---

### Post by jeremy31 on 2023-07-10
If I could have figured out what in in that kernel that I didn't add to the 5.19 source code.  Can you post results for ```
sudo dmesg | egrep -i 'blue|firm'; sudo cat /sys/kernel/debug/usb/devices | awk '/3571/' RS=
```

---

### Post by jsn33 on 2023-07-11
Yeah, sure. After reboot headset has no sound again. 
```
[    0.107154] Spectre V2 : Enabling Speculation Barrier for firmware calls
[    0.283575] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    0.292487] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-7f] only partially covers this bridge
[    1.487953] usb 3-2: Product: Bluetooth Radio
[    2.678125] Bluetooth: Core ver 2.22
[    2.678157] NET: Registered PF_BLUETOOTH protocol family
[    2.678158] Bluetooth: HCI device and connection manager initialized
[    2.678163] Bluetooth: HCI socket layer initialized
[    2.678165] Bluetooth: L2CAP socket layer initialized
[    2.678169] Bluetooth: SCO socket layer initialized
[    2.857925] Bluetooth: hci0: RTL: examining hci_ver=0b hci_rev=000b lmp_ver=0b lmp_subver=8852
[    2.859876] Bluetooth: hci0: RTL: rom_version status=0 version=1
[    2.859886] Bluetooth: hci0: RTL: loading rtl_bt/rtl8852bu_fw.bin
[    2.861748] Bluetooth: hci0: RTL: loading rtl_bt/rtl8852bu_config.bin
[    2.861890] Bluetooth: hci0: RTL: cfg_sz 6, total sz 38955
[    2.877209] rtw89_8852be 0000:02:00.0: Direct firmware load for rtw89/rtw8852b_fw-1.bin failed with error -2
[    2.877467] rtw89_8852be 0000:02:00.0: loaded firmware rtw89/rtw8852b_fw.bin
[    2.906371] rtw89_8852be 0000:02:00.0: Firmware version 0.27.32.1, cmd version 0, type 1
[    2.906380] rtw89_8852be 0000:02:00.0: Firmware version 0.27.32.1, cmd version 0, type 3
[    3.260894] Bluetooth: hci0: RTL: fw version 0xdfb791cb
[    3.396886] Bluetooth: hci0: Failed to read codec capabilities (-22)
[    3.411884] Bluetooth: hci0: AOSP extensions version v0.96
[    3.411887] Bluetooth: hci0: AOSP quality report is not supported
[    4.802836] [drm] Loading DMUB firmware via PSP: version=0x0101001F
[    4.803690] [drm] Found VCN firmware Version ENC: 1.16 DEC: 5 VEP: 0 Revision: 3
[    4.803705] amdgpu 0000:04:00.0: amdgpu: Will use PSP to load VCN firmware
[    4.877753] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.877762] Bluetooth: BNEP filters: protocol multicast
[    4.877769] Bluetooth: BNEP socket layer initialized
[    4.879503] Bluetooth: MGMT ver 1.22
[    4.943718] Bluetooth: RFCOMM TTY layer initialized
[    4.943737] Bluetooth: RFCOMM socket layer initialized
[    4.943746] Bluetooth: RFCOMM ver 1.11
T:  Bus=03 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=12   MxCh= 0
D:  Ver= 1.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=13d3 ProdID=3571 Rev= 0.00
S:  Manufacturer=Realtek
S:  Product=Bluetooth Radio
S:  SerialNumber=00e04c000001
C:* #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=500mA
I:* If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=81(I) Atr=03(Int.) MxPS=  16 Ivl=1ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
I:* If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=03(O) Atr=01(Isoc) MxPS=   0 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=   0 Ivl=1ms
I:  If#= 1 Alt= 1 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=03(O) Atr=01(Isoc) MxPS=   9 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=   9 Ivl=1ms
I:  If#= 1 Alt= 2 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=03(O) Atr=01(Isoc) MxPS=  17 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  17 Ivl=1ms
I:  If#= 1 Alt= 3 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=03(O) Atr=01(Isoc) MxPS=  25 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  25 Ivl=1ms
I:  If#= 1 Alt= 4 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=03(O) Atr=01(Isoc) MxPS=  33 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  33 Ivl=1ms
I:  If#= 1 Alt= 5 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
E:  Ad=03(O) Atr=01(Isoc) MxPS=  49 Ivl=1ms
E:  Ad=83(I) Atr=01(Isoc) MxPS=  49 Ivl=1ms

```

---

