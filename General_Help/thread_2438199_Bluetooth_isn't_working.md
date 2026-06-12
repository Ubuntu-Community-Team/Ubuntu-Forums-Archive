---
title: "Bluetooth isn't working"
date: 2020-03-07
forum: General Help
---

### Post by stanchata on 2020-03-07
Im using Ubuntu 19.10 and no device can detect my ubuntu machine and no device can be detected by my ubuntu machine. Ive tried a number of fixes for previous versions of ubuntu but nothing works :(

---

### Post by jeremy31 on 2020-03-07
Please post results from terminal for ```
lspci -nnk | grep -iA3 net; lsusb; dmesg | egrep -i 'blue|firm'
```

---

### Post by stanchata on 2020-03-07
```
02:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8172 Fast Ethernet [1969:10a0] (rev 10)
	Subsystem: Lenovo QCA8172 Fast Ethernet [17aa:3802]
	Kernel driver in use: alx
	Kernel modules: alx
03:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Lenovo BCM43142 802.11b/g/n [17aa:0611]
	Kernel driver in use: wl
	Kernel modules: wl
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 012: ID 105b:e065 Foxconn International, Inc. BCM43142A0 Bluetooth module
Bus 001 Device 003: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 174f:148d Syntek Lenovo EasyCamera
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    0.106095] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    0.132027] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[   20.809266] Bluetooth: Core ver 2.22
[   20.809286] Bluetooth: HCI device and connection manager initialized
[   20.809290] Bluetooth: HCI socket layer initialized
[   20.809292] Bluetooth: L2CAP socket layer initialized
[   20.809295] Bluetooth: SCO socket layer initialized
[   22.330635] Bluetooth: hci0: BCM: chip id 70
[   22.331619] Bluetooth: hci0: BCM: features 0x06
[   22.347634] Bluetooth: hci0: BCM43142A
[   22.348620] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0000
[   22.609758] bluetooth hci0: Direct firmware load for brcm/BCM43142A0-105b-e065.hcd failed with error -2
[   22.609762] Bluetooth: hci0: BCM: Patch brcm/BCM43142A0-105b-e065.hcd not found
[   24.620683] Bluetooth: hci0: command 0x1003 tx timeout
[   24.621697] Bluetooth: hci0: unexpected event for opcode 0x1003
[   24.878291] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[   46.765584] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   46.765587] Bluetooth: BNEP filters: protocol multicast
[   46.765595] Bluetooth: BNEP socket layer initialized
[   71.136865] Bluetooth: RFCOMM TTY layer initialized
[   71.136874] Bluetooth: RFCOMM socket layer initialized
[   71.136883] Bluetooth: RFCOMM ver 1.11
[  227.009933] audit: type=1107 audit(1583577112.850:51): pid=769 uid=103 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/" interface="org.freedesktop.DBus.ObjectManager" member="GetManagedObjects" mask="send" name="org.bluez" pid=2285 label="snap.chromium.chromium" peer_pid=766 peer_label="unconfined"
[ 1454.757623] Bluetooth: hci0: command 0x1003 tx timeout
[ 1454.759182] Bluetooth: hci0: unexpected event for opcode 0x1003
[ 1476.146080] Bluetooth: hci0: BCM: chip id 70
[ 1476.147078] Bluetooth: hci0: BCM: features 0x06
[ 1476.163061] Bluetooth: hci0: ivan-Lenovo-G500
[ 1476.164021] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0000
[ 1476.164127] bluetooth hci0: Direct firmware load for brcm/BCM43142A0-105b-e065.hcd failed with error -2
[ 1476.164131] Bluetooth: hci0: BCM: Patch brcm/BCM43142A0-105b-e065.hcd not found
[ 1478.180130] Bluetooth: hci0: command 0x1003 tx timeout
[ 1478.181067] Bluetooth: hci0: unexpected event for opcode 0x1003
[ 1480.102065] Bluetooth: hci0: BCM: chip id 70
[ 1480.103036] Bluetooth: hci0: BCM: features 0x06
[ 1480.119047] Bluetooth: hci0: ivan-Lenovo-G500
[ 1480.120021] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0000
[ 1480.120063] bluetooth hci0: Direct firmware load for brcm/BCM43142A0-105b-e065.hcd failed with error -2
[ 1480.120068] Bluetooth: hci0: BCM: Patch brcm/BCM43142A0-105b-e065.hcd not found
[ 1482.147857] Bluetooth: hci0: command 0x1003 tx timeout
[ 1482.147881] Bluetooth: hci0: sending frame failed (-19)
[ 1484.163771] Bluetooth: hci0: command 0x1001 tx timeout
[ 1484.163814] Bluetooth: hci0: sending frame failed (-19)
[ 1486.179592] Bluetooth: hci0: command 0x1009 tx timeout
[ 1490.593928] Bluetooth: hci0: unexpected event for opcode 0x1003
[ 1490.705983] Bluetooth: hci0: BCM: chip id 70
[ 1490.706962] Bluetooth: hci0: BCM: features 0x06
[ 1490.722984] Bluetooth: hci0: ivan-Lenovo-G500
[ 1490.723985] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0000
[ 1490.724031] bluetooth hci0: Direct firmware load for brcm/BCM43142A0-105b-e065.hcd failed with error -2
[ 1490.724035] Bluetooth: hci0: BCM: Patch brcm/BCM43142A0-105b-e065.hcd not found
[ 1743.153962] Bluetooth: hci0: BCM: chip id 70
[ 1743.154967] Bluetooth: hci0: BCM: features 0x06
[ 1743.170967] Bluetooth: hci0: ivan-Lenovo-G500
[ 1743.171964] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0000
[ 1743.171987] bluetooth hci0: Direct firmware load for brcm/BCM43142A0-105b-e065.hcd failed with error -2
[ 1743.171990] Bluetooth: hci0: BCM: Patch brcm/BCM43142A0-105b-e065.hcd not found
[ 1745.203946] Bluetooth: hci0: command 0x1003 tx timeout
[ 1745.204932] Bluetooth: hci0: unexpected event for opcode 0x1003
[ 1757.746022] Bluetooth: hci0: BCM: chip id 70
[ 1757.746961] Bluetooth: hci0: BCM: features 0x06
[ 1757.762973] Bluetooth: hci0: ivan-Lenovo-G500
[ 1757.763984] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0000
[ 1757.764027] bluetooth hci0: Direct firmware load for brcm/BCM43142A0-105b-e065.hcd failed with error -2
[ 1757.764031] Bluetooth: hci0: BCM: Patch brcm/BCM43142A0-105b-e065.hcd not found
[ 1759.795157] Bluetooth: hci0: command 0x1003 tx timeout
[ 1759.795957] Bluetooth: hci0: unexpected event for opcode 0x1003
[ 1807.674708] Bluetooth: hci0: BCM: chip id 70
[ 1807.675706] Bluetooth: hci0: BCM: features 0x06
[ 1807.691718] Bluetooth: hci0: ivan-Lenovo-G500
[ 1807.695716] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0000
[ 1807.695749] bluetooth hci0: Direct firmware load for brcm/BCM43142A0-105b-e065.hcd failed with error -2
[ 1807.695752] Bluetooth: hci0: BCM: Patch brcm/BCM43142A0-105b-e065.hcd not found
[ 1809.712212] Bluetooth: hci0: command 0x1003 tx timeout
[ 1809.713702] Bluetooth: hci0: unexpected event for opcode 0x1003
[ 1970.175270] Modules linked in: uas usb_storage rfcomm cmac bnep nls_iso8859_1 intel_rapl_msr intel_rapl_common x86_pkg_temp_thermal intel_powerclamp amdgpu snd_hda_codec_hdmi snd_hda_codec_conexant snd_hda_codec_generic ledtrig_audio amd_iommu_v2 gpu_sched coretemp uvcvideo snd_hda_intel snd_hda_codec snd_hda_core kvm irqbypass snd_hwdep videobuf2_vmalloc rtsx_usb_ms mei_hdcp snd_pcm snd_seq_midi videobuf2_memops crct10dif_pclmul videobuf2_v4l2 crc32_pclmul snd_seq_midi_event ghash_clmulni_intel videobuf2_common snd_rawmidi videodev snd_seq memstick snd_seq_device btusb snd_timer snd cryptd btrtl intel_cstate btbcm btintel mc soundcore i915 radeon bluetooth wl(POE) ecdh_generic ecc ideapad_laptop sparse_keymap ttm drm_kms_helper cfg80211 drm i2c_algo_bit intel_rapl_perf fb_sys_fops syscopyarea sysfillrect wmi sysimgblt joydev input_leds mei_me mei mac_hid serio_raw sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 rtsx_usb_sdmmc rtsx_usb hid_generic usbhid hid ahci
[ 1977.239577] Modules linked in: uas usb_storage rfcomm cmac bnep nls_iso8859_1 intel_rapl_msr intel_rapl_common x86_pkg_temp_thermal intel_powerclamp amdgpu snd_hda_codec_hdmi snd_hda_codec_conexant snd_hda_codec_generic ledtrig_audio amd_iommu_v2 gpu_sched coretemp uvcvideo snd_hda_intel snd_hda_codec snd_hda_core kvm irqbypass snd_hwdep videobuf2_vmalloc rtsx_usb_ms mei_hdcp snd_pcm snd_seq_midi videobuf2_memops crct10dif_pclmul videobuf2_v4l2 crc32_pclmul snd_seq_midi_event ghash_clmulni_intel videobuf2_common snd_rawmidi videodev snd_seq memstick snd_seq_device btusb snd_timer snd cryptd btrtl intel_cstate btbcm btintel mc soundcore i915 radeon bluetooth wl(POE) ecdh_generic ecc ideapad_laptop sparse_keymap ttm drm_kms_helper cfg80211 drm i2c_algo_bit intel_rapl_perf fb_sys_fops syscopyarea sysfillrect wmi sysimgblt joydev input_leds mei_me mei mac_hid serio_raw sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 rtsx_usb_sdmmc rtsx_usb hid_generic usbhid hid ahci
[ 1981.438595] Modules linked in: uas usb_storage rfcomm cmac bnep nls_iso8859_1 intel_rapl_msr intel_rapl_common x86_pkg_temp_thermal intel_powerclamp amdgpu snd_hda_codec_hdmi snd_hda_codec_conexant snd_hda_codec_generic ledtrig_audio amd_iommu_v2 gpu_sched coretemp uvcvideo snd_hda_intel snd_hda_codec snd_hda_core kvm irqbypass snd_hwdep videobuf2_vmalloc rtsx_usb_ms mei_hdcp snd_pcm snd_seq_midi videobuf2_memops crct10dif_pclmul videobuf2_v4l2 crc32_pclmul snd_seq_midi_event ghash_clmulni_intel videobuf2_common snd_rawmidi videodev snd_seq memstick snd_seq_device btusb snd_timer snd cryptd btrtl intel_cstate btbcm btintel mc soundcore i915 radeon bluetooth wl(POE) ecdh_generic ecc ideapad_laptop sparse_keymap ttm drm_kms_helper cfg80211 drm i2c_algo_bit intel_rapl_perf fb_sys_fops syscopyarea sysfillrect wmi sysimgblt joydev input_leds mei_me mei mac_hid serio_raw sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 rtsx_usb_sdmmc rtsx_usb hid_generic usbhid hid ahci
[ 1985.638400] Modules linked in: uas usb_storage rfcomm cmac bnep nls_iso8859_1 intel_rapl_msr intel_rapl_common x86_pkg_temp_thermal intel_powerclamp amdgpu snd_hda_codec_hdmi snd_hda_codec_conexant snd_hda_codec_generic ledtrig_audio amd_iommu_v2 gpu_sched coretemp uvcvideo snd_hda_intel snd_hda_codec snd_hda_core kvm irqbypass snd_hwdep videobuf2_vmalloc rtsx_usb_ms mei_hdcp snd_pcm snd_seq_midi videobuf2_memops crct10dif_pclmul videobuf2_v4l2 crc32_pclmul snd_seq_midi_event ghash_clmulni_intel videobuf2_common snd_rawmidi videodev snd_seq memstick snd_seq_device btusb snd_timer snd cryptd btrtl intel_cstate btbcm btintel mc soundcore i915 radeon bluetooth wl(POE) ecdh_generic ecc ideapad_laptop sparse_keymap ttm drm_kms_helper cfg80211 drm i2c_algo_bit intel_rapl_perf fb_sys_fops syscopyarea sysfillrect wmi sysimgblt joydev input_leds mei_me mei mac_hid serio_raw sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 rtsx_usb_sdmmc rtsx_usb hid_generic usbhid hid ahci
[ 1989.938092] Modules linked in: uas usb_storage rfcomm cmac bnep nls_iso8859_1 intel_rapl_msr intel_rapl_common x86_pkg_temp_thermal intel_powerclamp amdgpu snd_hda_codec_hdmi snd_hda_codec_conexant snd_hda_codec_generic ledtrig_audio amd_iommu_v2 gpu_sched coretemp uvcvideo snd_hda_intel snd_hda_codec snd_hda_core kvm irqbypass snd_hwdep videobuf2_vmalloc rtsx_usb_ms mei_hdcp snd_pcm snd_seq_midi videobuf2_memops crct10dif_pclmul videobuf2_v4l2 crc32_pclmul snd_seq_midi_event ghash_clmulni_intel videobuf2_common snd_rawmidi videodev snd_seq memstick snd_seq_device btusb snd_timer snd cryptd btrtl intel_cstate btbcm btintel mc soundcore i915 radeon bluetooth wl(POE) ecdh_generic ecc ideapad_laptop sparse_keymap ttm drm_kms_helper cfg80211 drm i2c_algo_bit intel_rapl_perf fb_sys_fops syscopyarea sysfillrect wmi sysimgblt joydev input_leds mei_me mei mac_hid serio_raw sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 rtsx_usb_sdmmc rtsx_usb hid_generic usbhid hid ahci
[ 1994.137869] Modules linked in: uas usb_storage rfcomm cmac bnep nls_iso8859_1 intel_rapl_msr intel_rapl_common x86_pkg_temp_thermal intel_powerclamp amdgpu snd_hda_codec_hdmi snd_hda_codec_conexant snd_hda_codec_generic ledtrig_audio amd_iommu_v2 gpu_sched coretemp uvcvideo snd_hda_intel snd_hda_codec snd_hda_core kvm irqbypass snd_hwdep videobuf2_vmalloc rtsx_usb_ms mei_hdcp snd_pcm snd_seq_midi videobuf2_memops crct10dif_pclmul videobuf2_v4l2 crc32_pclmul snd_seq_midi_event ghash_clmulni_intel videobuf2_common snd_rawmidi videodev snd_seq memstick snd_seq_device btusb snd_timer snd cryptd btrtl intel_cstate btbcm btintel mc soundcore i915 radeon bluetooth wl(POE) ecdh_generic ecc ideapad_laptop sparse_keymap ttm drm_kms_helper cfg80211 drm i2c_algo_bit intel_rapl_perf fb_sys_fops syscopyarea sysfillrect wmi sysimgblt joydev input_leds mei_me mei mac_hid serio_raw sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 rtsx_usb_sdmmc rtsx_usb hid_generic usbhid hid ahci
[ 1998.333714] Modules linked in: uas usb_storage rfcomm cmac bnep nls_iso8859_1 intel_rapl_msr intel_rapl_common x86_pkg_temp_thermal intel_powerclamp amdgpu snd_hda_codec_hdmi snd_hda_codec_conexant snd_hda_codec_generic ledtrig_audio amd_iommu_v2 gpu_sched coretemp uvcvideo snd_hda_intel snd_hda_codec snd_hda_core kvm irqbypass snd_hwdep videobuf2_vmalloc rtsx_usb_ms mei_hdcp snd_pcm snd_seq_midi videobuf2_memops crct10dif_pclmul videobuf2_v4l2 crc32_pclmul snd_seq_midi_event ghash_clmulni_intel videobuf2_common snd_rawmidi videodev snd_seq memstick snd_seq_device btusb snd_timer snd cryptd btrtl intel_cstate btbcm btintel mc soundcore i915 radeon bluetooth wl(POE) ecdh_generic ecc ideapad_laptop sparse_keymap ttm drm_kms_helper cfg80211 drm i2c_algo_bit intel_rapl_perf fb_sys_fops syscopyarea sysfillrect wmi sysimgblt joydev input_leds mei_me mei mac_hid serio_raw sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 rtsx_usb_sdmmc rtsx_usb hid_generic usbhid hid ahci
[ 2002.533562] Modules linked in: uas usb_storage rfcomm cmac bnep nls_iso8859_1 intel_rapl_msr intel_rapl_common x86_pkg_temp_thermal intel_powerclamp amdgpu snd_hda_codec_hdmi snd_hda_codec_conexant snd_hda_codec_generic ledtrig_audio amd_iommu_v2 gpu_sched coretemp uvcvideo snd_hda_intel snd_hda_codec snd_hda_core kvm irqbypass snd_hwdep videobuf2_vmalloc rtsx_usb_ms mei_hdcp snd_pcm snd_seq_midi videobuf2_memops crct10dif_pclmul videobuf2_v4l2 crc32_pclmul snd_seq_midi_event ghash_clmulni_intel videobuf2_common snd_rawmidi videodev snd_seq memstick snd_seq_device btusb snd_timer snd cryptd btrtl intel_cstate btbcm btintel mc soundcore i915 radeon bluetooth wl(POE) ecdh_generic ecc ideapad_laptop sparse_keymap ttm drm_kms_helper cfg80211 drm i2c_algo_bit intel_rapl_perf fb_sys_fops syscopyarea sysfillrect wmi sysimgblt joydev input_leds mei_me mei mac_hid serio_raw sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 rtsx_usb_sdmmc rtsx_usb hid_generic usbhid hid ahci
[ 2006.833137] Modules linked in: uas usb_storage rfcomm cmac bnep nls_iso8859_1 intel_rapl_msr intel_rapl_common x86_pkg_temp_thermal intel_powerclamp amdgpu snd_hda_codec_hdmi snd_hda_codec_conexant snd_hda_codec_generic ledtrig_audio amd_iommu_v2 gpu_sched coretemp uvcvideo snd_hda_intel snd_hda_codec snd_hda_core kvm irqbypass snd_hwdep videobuf2_vmalloc rtsx_usb_ms mei_hdcp snd_pcm snd_seq_midi videobuf2_memops crct10dif_pclmul videobuf2_v4l2 crc32_pclmul snd_seq_midi_event ghash_clmulni_intel videobuf2_common snd_rawmidi videodev snd_seq memstick snd_seq_device btusb snd_timer snd cryptd btrtl intel_cstate btbcm btintel mc soundcore i915 radeon bluetooth wl(POE) ecdh_generic ecc ideapad_laptop sparse_keymap ttm drm_kms_helper cfg80211 drm i2c_algo_bit intel_rapl_perf fb_sys_fops syscopyarea sysfillrect wmi sysimgblt joydev input_leds mei_me mei mac_hid serio_raw sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 rtsx_usb_sdmmc rtsx_usb hid_generic usbhid hid ahci
[ 2011.032952] Modules linked in: hid_logitech_hidpp hid_logitech_dj uas usb_storage rfcomm cmac bnep nls_iso8859_1 intel_rapl_msr intel_rapl_common x86_pkg_temp_thermal intel_powerclamp amdgpu snd_hda_codec_hdmi snd_hda_codec_conexant snd_hda_codec_generic ledtrig_audio amd_iommu_v2 gpu_sched coretemp uvcvideo snd_hda_intel snd_hda_codec snd_hda_core kvm irqbypass snd_hwdep videobuf2_vmalloc rtsx_usb_ms mei_hdcp snd_pcm snd_seq_midi videobuf2_memops crct10dif_pclmul videobuf2_v4l2 crc32_pclmul snd_seq_midi_event ghash_clmulni_intel videobuf2_common snd_rawmidi videodev snd_seq memstick snd_seq_device btusb snd_timer snd cryptd btrtl intel_cstate btbcm btintel mc soundcore i915 radeon bluetooth wl(POE) ecdh_generic ecc ideapad_laptop sparse_keymap ttm drm_kms_helper cfg80211 drm i2c_algo_bit intel_rapl_perf fb_sys_fops syscopyarea sysfillrect wmi sysimgblt joydev input_leds mei_me mei mac_hid serio_raw sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 rtsx_usb_sdmmc rtsx_usb
[ 2015.232722] Modules linked in: hid_logitech_hidpp hid_logitech_dj uas usb_storage rfcomm cmac bnep nls_iso8859_1 intel_rapl_msr intel_rapl_common x86_pkg_temp_thermal intel_powerclamp amdgpu snd_hda_codec_hdmi snd_hda_codec_conexant snd_hda_codec_generic ledtrig_audio amd_iommu_v2 gpu_sched coretemp uvcvideo snd_hda_intel snd_hda_codec snd_hda_core kvm irqbypass snd_hwdep videobuf2_vmalloc rtsx_usb_ms mei_hdcp snd_pcm snd_seq_midi videobuf2_memops crct10dif_pclmul videobuf2_v4l2 crc32_pclmul snd_seq_midi_event ghash_clmulni_intel videobuf2_common snd_rawmidi videodev snd_seq memstick snd_seq_device btusb snd_timer snd cryptd btrtl intel_cstate btbcm btintel mc soundcore i915 radeon bluetooth wl(POE) ecdh_generic ecc ideapad_laptop sparse_keymap ttm drm_kms_helper cfg80211 drm i2c_algo_bit intel_rapl_perf fb_sys_fops syscopyarea sysfillrect wmi sysimgblt joydev input_leds mei_me mei mac_hid serio_raw sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 rtsx_usb_sdmmc rtsx_usb
[ 2019.532423] Modules linked in: hid_logitech_hidpp hid_logitech_dj uas usb_storage rfcomm cmac bnep nls_iso8859_1 intel_rapl_msr intel_rapl_common x86_pkg_temp_thermal intel_powerclamp amdgpu snd_hda_codec_hdmi snd_hda_codec_conexant snd_hda_codec_generic ledtrig_audio amd_iommu_v2 gpu_sched coretemp uvcvideo snd_hda_intel snd_hda_codec snd_hda_core kvm irqbypass snd_hwdep videobuf2_vmalloc rtsx_usb_ms mei_hdcp snd_pcm snd_seq_midi videobuf2_memops crct10dif_pclmul videobuf2_v4l2 crc32_pclmul snd_seq_midi_event ghash_clmulni_intel videobuf2_common snd_rawmidi videodev snd_seq memstick snd_seq_device btusb snd_timer snd cryptd btrtl intel_cstate btbcm btintel mc soundcore i915 radeon bluetooth wl(POE) ecdh_generic ecc ideapad_laptop sparse_keymap ttm drm_kms_helper cfg80211 drm i2c_algo_bit intel_rapl_perf fb_sys_fops syscopyarea sysfillrect wmi sysimgblt joydev input_leds mei_me mei mac_hid serio_raw sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 rtsx_usb_sdmmc rtsx_usb
[ 2023.728517] Modules linked in: hid_logitech_hidpp hid_logitech_dj uas usb_storage rfcomm cmac bnep nls_iso8859_1 intel_rapl_msr intel_rapl_common x86_pkg_temp_thermal intel_powerclamp amdgpu snd_hda_codec_hdmi snd_hda_codec_conexant snd_hda_codec_generic ledtrig_audio amd_iommu_v2 gpu_sched coretemp uvcvideo snd_hda_intel snd_hda_codec snd_hda_core kvm irqbypass snd_hwdep videobuf2_vmalloc rtsx_usb_ms mei_hdcp snd_pcm snd_seq_midi videobuf2_memops crct10dif_pclmul videobuf2_v4l2 crc32_pclmul snd_seq_midi_event ghash_clmulni_intel videobuf2_common snd_rawmidi videodev snd_seq memstick snd_seq_device btusb snd_timer snd cryptd btrtl intel_cstate btbcm btintel mc soundcore i915 radeon bluetooth wl(POE) ecdh_generic ecc ideapad_laptop sparse_keymap ttm drm_kms_helper cfg80211 drm i2c_algo_bit intel_rapl_perf fb_sys_fops syscopyarea sysfillrect wmi sysimgblt joydev input_leds mei_me mei mac_hid serio_raw sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 rtsx_usb_sdmmc rtsx_usb
[ 2027.927922] Modules linked in: hid_logitech_hidpp hid_logitech_dj uas usb_storage rfcomm cmac bnep nls_iso8859_1 intel_rapl_msr intel_rapl_common x86_pkg_temp_thermal intel_powerclamp amdgpu snd_hda_codec_hdmi snd_hda_codec_conexant snd_hda_codec_generic ledtrig_audio amd_iommu_v2 gpu_sched coretemp uvcvideo snd_hda_intel snd_hda_codec snd_hda_core kvm irqbypass snd_hwdep videobuf2_vmalloc rtsx_usb_ms mei_hdcp snd_pcm snd_seq_midi videobuf2_memops crct10dif_pclmul videobuf2_v4l2 crc32_pclmul snd_seq_midi_event ghash_clmulni_intel videobuf2_common snd_rawmidi videodev snd_seq memstick snd_seq_device btusb snd_timer snd cryptd btrtl intel_cstate btbcm btintel mc soundcore i915 radeon bluetooth wl(POE) ecdh_generic ecc ideapad_laptop sparse_keymap ttm drm_kms_helper cfg80211 drm i2c_algo_bit intel_rapl_perf fb_sys_fops syscopyarea sysfillrect wmi sysimgblt joydev input_leds mei_me mei mac_hid serio_raw sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 rtsx_usb_sdmmc rtsx_usb
[ 2032.231739] Modules linked in: hid_logitech_hidpp hid_logitech_dj uas usb_storage rfcomm cmac bnep nls_iso8859_1 intel_rapl_msr intel_rapl_common x86_pkg_temp_thermal intel_powerclamp amdgpu snd_hda_codec_hdmi snd_hda_codec_conexant snd_hda_codec_generic ledtrig_audio amd_iommu_v2 gpu_sched coretemp uvcvideo snd_hda_intel snd_hda_codec snd_hda_core kvm irqbypass snd_hwdep videobuf2_vmalloc rtsx_usb_ms mei_hdcp snd_pcm snd_seq_midi videobuf2_memops crct10dif_pclmul videobuf2_v4l2 crc32_pclmul snd_seq_midi_event ghash_clmulni_intel videobuf2_common snd_rawmidi videodev snd_seq memstick snd_seq_device btusb snd_timer snd cryptd btrtl intel_cstate btbcm btintel mc soundcore i915 radeon bluetooth wl(POE) ecdh_generic ecc ideapad_laptop sparse_keymap ttm drm_kms_helper cfg80211 drm i2c_algo_bit intel_rapl_perf fb_sys_fops syscopyarea sysfillrect wmi sysimgblt joydev input_leds mei_me mei mac_hid serio_raw sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 rtsx_usb_sdmmc rtsx_usb
[ 2036.427410] Modules linked in: hid_logitech_hidpp hid_logitech_dj uas usb_storage rfcomm cmac bnep nls_iso8859_1 intel_rapl_msr intel_rapl_common x86_pkg_temp_thermal intel_powerclamp amdgpu snd_hda_codec_hdmi snd_hda_codec_conexant snd_hda_codec_generic ledtrig_audio amd_iommu_v2 gpu_sched coretemp uvcvideo snd_hda_intel snd_hda_codec snd_hda_core kvm irqbypass snd_hwdep videobuf2_vmalloc rtsx_usb_ms mei_hdcp snd_pcm snd_seq_midi videobuf2_memops crct10dif_pclmul videobuf2_v4l2 crc32_pclmul snd_seq_midi_event ghash_clmulni_intel videobuf2_common snd_rawmidi videodev snd_seq memstick snd_seq_device btusb snd_timer snd cryptd btrtl intel_cstate btbcm btintel mc soundcore i915 radeon bluetooth wl(POE) ecdh_generic ecc ideapad_laptop sparse_keymap ttm drm_kms_helper cfg80211 drm i2c_algo_bit intel_rapl_perf fb_sys_fops syscopyarea sysfillrect wmi sysimgblt joydev input_leds mei_me mei mac_hid serio_raw sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 rtsx_usb_sdmmc rtsx_usb
[ 2040.627209] Modules linked in: hid_logitech_hidpp hid_logitech_dj uas usb_storage rfcomm cmac bnep nls_iso8859_1 intel_rapl_msr intel_rapl_common x86_pkg_temp_thermal intel_powerclamp amdgpu snd_hda_codec_hdmi snd_hda_codec_conexant snd_hda_codec_generic ledtrig_audio amd_iommu_v2 gpu_sched coretemp uvcvideo snd_hda_intel snd_hda_codec snd_hda_core kvm irqbypass snd_hwdep videobuf2_vmalloc rtsx_usb_ms mei_hdcp snd_pcm snd_seq_midi videobuf2_memops crct10dif_pclmul videobuf2_v4l2 crc32_pclmul snd_seq_midi_event ghash_clmulni_intel videobuf2_common snd_rawmidi videodev snd_seq memstick snd_seq_device btusb snd_timer snd cryptd btrtl intel_cstate btbcm btintel mc soundcore i915 radeon bluetooth wl(POE) ecdh_generic ecc ideapad_laptop sparse_keymap ttm drm_kms_helper cfg80211 drm i2c_algo_bit intel_rapl_perf fb_sys_fops syscopyarea sysfillrect wmi sysimgblt joydev input_leds mei_me mei mac_hid serio_raw sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 rtsx_usb_sdmmc rtsx_usb
[ 2044.926952] Modules linked in: hid_logitech_hidpp hid_logitech_dj uas usb_storage rfcomm cmac bnep nls_iso8859_1 intel_rapl_msr intel_rapl_common x86_pkg_temp_thermal intel_powerclamp amdgpu snd_hda_codec_hdmi snd_hda_codec_conexant snd_hda_codec_generic ledtrig_audio amd_iommu_v2 gpu_sched coretemp uvcvideo snd_hda_intel snd_hda_codec snd_hda_core kvm irqbypass snd_hwdep videobuf2_vmalloc rtsx_usb_ms mei_hdcp snd_pcm snd_seq_midi videobuf2_memops crct10dif_pclmul videobuf2_v4l2 crc32_pclmul snd_seq_midi_event ghash_clmulni_intel videobuf2_common snd_rawmidi videodev snd_seq memstick snd_seq_device btusb snd_timer snd cryptd btrtl intel_cstate btbcm btintel mc soundcore i915 radeon bluetooth wl(POE) ecdh_generic ecc ideapad_laptop sparse_keymap ttm drm_kms_helper cfg80211 drm i2c_algo_bit intel_rapl_perf fb_sys_fops syscopyarea sysfillrect wmi sysimgblt joydev input_leds mei_me mei mac_hid serio_raw sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 rtsx_usb_sdmmc rtsx_usb
[ 2049.226701] Modules linked in: hid_logitech_hidpp hid_logitech_dj uas usb_storage rfcomm cmac bnep nls_iso8859_1 intel_rapl_msr intel_rapl_common x86_pkg_temp_thermal intel_powerclamp amdgpu snd_hda_codec_hdmi snd_hda_codec_conexant snd_hda_codec_generic ledtrig_audio amd_iommu_v2 gpu_sched coretemp uvcvideo snd_hda_intel snd_hda_codec snd_hda_core kvm irqbypass snd_hwdep videobuf2_vmalloc rtsx_usb_ms mei_hdcp snd_pcm snd_seq_midi videobuf2_memops crct10dif_pclmul videobuf2_v4l2 crc32_pclmul snd_seq_midi_event ghash_clmulni_intel videobuf2_common snd_rawmidi videodev snd_seq memstick snd_seq_device btusb snd_timer snd cryptd btrtl intel_cstate btbcm btintel mc soundcore i915 radeon bluetooth wl(POE) ecdh_generic ecc ideapad_laptop sparse_keymap ttm drm_kms_helper cfg80211 drm i2c_algo_bit intel_rapl_perf fb_sys_fops syscopyarea sysfillrect wmi sysimgblt joydev input_leds mei_me mei mac_hid serio_raw sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 rtsx_usb_sdmmc rtsx_usb
[ 2053.426493] Modules linked in: hid_logitech_hidpp hid_logitech_dj uas usb_storage rfcomm cmac bnep nls_iso8859_1 intel_rapl_msr intel_rapl_common x86_pkg_temp_thermal intel_powerclamp amdgpu snd_hda_codec_hdmi snd_hda_codec_conexant snd_hda_codec_generic ledtrig_audio amd_iommu_v2 gpu_sched coretemp uvcvideo snd_hda_intel snd_hda_codec snd_hda_core kvm irqbypass snd_hwdep videobuf2_vmalloc rtsx_usb_ms mei_hdcp snd_pcm snd_seq_midi videobuf2_memops crct10dif_pclmul videobuf2_v4l2 crc32_pclmul snd_seq_midi_event ghash_clmulni_intel videobuf2_common snd_rawmidi videodev snd_seq memstick snd_seq_device btusb snd_timer snd cryptd btrtl intel_cstate btbcm btintel mc soundcore i915 radeon bluetooth wl(POE) ecdh_generic ecc ideapad_laptop sparse_keymap ttm drm_kms_helper cfg80211 drm i2c_algo_bit intel_rapl_perf fb_sys_fops syscopyarea sysfillrect wmi sysimgblt joydev input_leds mei_me mei mac_hid serio_raw sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 rtsx_usb_sdmmc rtsx_usb
[ 2371.255518] audit: type=1107 audit(1583579257.204:54): pid=769 uid=103 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/" interface="org.freedesktop.DBus.ObjectManager" member="GetManagedObjects" mask="send" name="org.bluez" pid=6712 label="snap.chromium.chromium" peer_pid=5907 peer_label="unconfined"
[ 2371.261381] audit: type=1107 audit(1583579257.208:55): pid=769 uid=103 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/" interface="org.freedesktop.DBus.ObjectManager" member="GetManagedObjects" mask="send" name="org.bluez" pid=6658 label="snap.chromium.chromium" peer_pid=5907 peer_label="unconfined"
[ 2371.261723] audit: type=1107 audit(1583579257.208:56): pid=769 uid=103 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/" interface="org.freedesktop.DBus.ObjectManager" member="GetManagedObjects" mask="send" name="org.bluez" pid=6638 label="snap.chromium.chromium" peer_pid=5907 peer_label="unconfined"
[ 2764.336291] Bluetooth: hci0: BCM: chip id 70
[ 2764.338112] Bluetooth: hci0: BCM: features 0x06
[ 2764.354028] Bluetooth: hci0: ivan-Lenovo-G500
[ 2764.355001] Bluetooth: hci0: BCM43142A0 (001.001.011) build 0000
[ 2764.355037] bluetooth hci0: Direct firmware load for brcm/BCM43142A0-105b-e065.hcd failed with error -2
[ 2764.355041] Bluetooth: hci0: BCM: Patch brcm/BCM43142A0-105b-e065.hcd not found
[ 2766.390123] Bluetooth: hci0: command 0x1003 tx timeout
[ 2766.390982] Bluetooth: hci0: unexpected event for opcode 0x1003
```

---

### Post by jeremy31 on 2020-03-07
Try ```
cd /lib/firmware/brcm
sudo wget https://github.com/winterheart/broadcom-bt-firmware/raw/master/brcm/BCM43142A0-105b-e065.hcd
```
Shut down and boot

---

### Post by stanchata on 2020-03-07
Thank you so much!!! Everything is working now =d>:grin:

---

