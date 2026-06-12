---
title: "Broken BIOS"
date: 2022-11-02
forum: General Help
---

### Post by zkab on 2022-11-02
I have Ubuntu 22.10 (Linux 5.19.0) and got following (IRQ & CCP) in dmsg:
```
sudo dmesg | grep -i ccp
[    3.617750] ccp 0000:05:00.2: enabling device (0000 -> 0002)
[    3.617756] ccp 0000:05:00.2: can't find IRQ for PCI INT C; please try using pci=biosirq
[    3.617800] ccp 0000:05:00.2: ccp: unable to access the device: you might be running a broken BIOS.
[    3.652437] ccp 0000:05:00.2: tee enabled
[    3.652440] ccp 0000:05:00.2: psp enabled
[    5.877234] Modules linked in: binfmt_misc sunrpc amdgpu(+) intel_rapl_msr nls_iso8859_1 intel_rapl_common mt7921e mt7921_common edac_mce_amd mt76_connac_lib mt76 kvm_amd snd_sof_amd_renoir snd_hda_codec_realtek snd_hda_codec_generic ledtrig_audio snd_sof_amd_acp snd_hda_codec_hdmi snd_sof_pci snd_hda_intel snd_intel_dspcfg snd_intel_sdw_acpi snd_hda_codec snd_hda_core snd_hwdep mac80211 btusb btrtl btbcm btintel btmtk snd_seq_midi snd_sof snd_seq_midi_event snd_sof_utils kvm iommu_v2 snd_rawmidi gpu_sched drm_ttm_helper crct10dif_pclmul ttm snd_soc_core snd_compress ac97_bus snd_pcm_dmaengine snd_pci_ps snd_acp_pci ghash_clmulni_intel bluetooth snd_seq snd_pci_acp6x drm_display_helper ecdh_generic cec ecc snd_pcm joydev rc_core snd_seq_device aesni_intel input_leds crypto_simd mac_hid cryptd cfg80211 snd_timer rapl snd drm_kms_helper snd_pci_acp5x i2c_algo_bit snd_rn_pci_acp3x fb_sys_fops snd_acp_config syscopyarea sysfillrect snd_soc_acpi sysimgblt snd_pci_acp3x soundcore k10temp ccp 
```
My BIOS looks like this:
```
BIOS Information
	Vendor: American Megatrends International, LLC.
	Version: GTR_V1.24_bLink_P4C5M43
	Release Date: 06/08/2022
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 0 MB
	Characteristics:
		PCI is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		Japanese floppy for NEC 9800 1.2 MB is supported (int 13h)
		Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
		5.25"/360 kB floppy services are supported (int 13h)
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 kB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		BIOS boot specification is supported
		Targeted content distribution is supported
		UEFI is supported
	BIOS Revision: 5.19

BIOS Language Information
	Language Description Format: Long
	Installable Languages: 1
		en|US|iso8859-1
	Currently Installed Language: en|US|iso8859-1
```
I have set acpi=off in /etc/default/grub since I got following errors in every reboot:
```
[    0.776099] ACPI Error: No handler for Region [ECRM] (000000001f075226) [EmbeddedControl] (20220331/evregion-130)
[    0.776605] ACPI Error: Region EmbeddedControl (ID=3) has no handler (20220331/exfldio-261)
[    0.776625] ACPI Error: Aborting method \_SB.GPIO._EVT due to previous error (AE_NOT_EXIST) (20220331/psparse-529) 
```
I am confused how to proceed.
According to support BIOS Rev 5.19 is the latest one ...

---

### Post by ActionParsnip on 2022-11-02
Seems you aren't alone
[https://forums.lenovo.com/t5/Other-Linux-Discussions/ACPI-Error-No-handler-for-Region-ECSI-on-E14-AMD-Gen-4/m-p/5169242](https://forums.lenovo.com/t5/Other-Linux-Discussions/ACPI-Error-No-handler-for-Region-ECSI-on-E14-AMD-Gen-4/m-p/5169242)

---

### Post by ActionParsnip on 2022-11-02
[https://unix.stackexchange.com/questions/575101/how-to-fix-acpi-error-no-handler-for-region-ecrm-debian](https://unix.stackexchange.com/questions/575101/how-to-fix-acpi-error-no-handler-for-region-ecrm-debian)

Try the boot option:
```

acpi=off

```

May help

---

### Post by oldfred on 2022-11-02
What brand/model system?
Is it a Pluton based system?

Lenovo's new AMD Rembrandt powered laptops with Microsoft Pluton security co-processor are set by default to only trust Microsoft's key or the only boot Windows. ThinkPad Z13 
[https://www.phoronix.com/scan.php?page=news_item&px=Lenovo-Pluton-Windows-Default](https://www.phoronix.com/scan.php?page=news_item&px=Lenovo-Pluton-Windows-Default)
Lenovo with Linux support (says Z13 has UEFI setting to turn off  Pluton)
[https://www.phoronix.com/news/Lenovo-Linux-2022-State](https://www.phoronix.com/news/Lenovo-Linux-2022-State)

---

### Post by aug7744 on 2022-11-02
Disable secure boot.
Try enable firmware in BIOS mode and if have ACPI option select the last version.

---

### Post by zkab on 2022-11-06
I have Beelink GTR5 5900HX

[https://www.bee-link.com/catalog/product/index?id=364](https://www.bee-link.com/catalog/product/index?id=364)

and have set in BIOS (version: GTR_V1.24_bLink_P4C5M43):

   acpi off
   secure boot off
   no legacy boot mode

but no change in messages from 'dmesg'.

Should I put back my head into the sand and pretend everything is OK or ...

---

