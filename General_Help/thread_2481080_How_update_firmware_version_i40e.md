---
title: "How update firmware version i40e"
date: 2022-11-18
forum: General Help
---

### Post by pelomorao on 2022-11-18
Hi, I just updated my i40e driver to version 2.20.12 and recommend updating the firmware to version 9.01 ([http://doc.dpdk.org/guides/nics/i40e.html#recommended-matching-list](http://doc.dpdk.org/guides/nics/i40e.html#recommended-matching-list)), currently I have firmware version 7.30. I have been looking for how to update the firmware but I can't find anything on google, could you help me? Thank you

---

### Post by oldfred on 2022-11-18
What brand/model system. 
Typically you download manual for your system from vendor & it has instructions on how to update UEFI firmware.
Many systems have several ways to update.
You can download update file, to FAT32 partition and from within UEFI load update. Or create a DOS bootable flash drive and run update.
Many automatically update if using Windows.

And now with Linux better systems support fwupdate.
[https://fwupd.org/](https://fwupd.org/)
Devices using LVFS for firmware updates
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)

Older systems that fwupdate does not support
[https://wiki.archlinux.org/title/Flashing_BIOS_from_Linux](https://wiki.archlinux.org/title/Flashing_BIOS_from_Linux)

---

### Post by pelomorao on 2022-11-19
Hello,


Thanks for answering, I already tried that option and it tells me that I don't have any firmware update, if I launch fwupdmgr update:


```
[COLOR=#000000][FONT=Menlo]Devices with no available firmware updates: [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] &#8226; MZVL2512HCJQ-00B07[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] &#8226; MZVL2512HCJQ-00B07[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]No updatable devices[/FONT][/COLOR]
```

I don't know if there is a way to force this update since as it says on the page that I link to in the main post, the recommended firmware is 9.0.1

PS: I have Ubuntu 22.04 and my network card is an X710 ([COLOR=#000000][FONT=Menlo]Ethernet controller [0200]: Intel Corporation Ethernet Controller X710 for 10GBASE-T [8086:15ff] (rev 02)[/FONT][/COLOR]) which is the driver that I updated (i40e Driver) and I am trying to update the firmware of my network card

[COLOR=#000000][FONT=Menlo]ethtool -i enp33s0f0[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Menlo]driver: i40e
[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]version: 2.20.12[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]firmware-version: 7.30 0x800083bd 1.2684.0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]expansion-rom-version: [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]bus-info: 0000:21:00.0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]supports-statistics: yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]supports-test: yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]supports-eeprom-access: yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]supports-register-dump: yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]supports-priv-flags: yes[/FONT][/COLOR]
```

---

### Post by oldfred on 2022-11-20
Ubuntu normally has current drivers.

Does this not say 7.0?
[https://www.intel.com/content/www/us/en/docs/programmable/683362/1-3-1/updating-the-xl710-firmware.html](https://www.intel.com/content/www/us/en/docs/programmable/683362/1-3-1/updating-the-xl710-firmware.html)

---

### Post by pelomorao on 2022-11-20
> **oldfred said:**
> Ubuntu normally has current drivers.

Does this not say 7.0?
[https://www.intel.com/content/www/us/en/docs/programmable/683362/1-3-1/updating-the-xl710-firmware.html](https://www.intel.com/content/www/us/en/docs/programmable/683362/1-3-1/updating-the-xl710-firmware.html)

Yes, it says so but with the i40e driver version 2.10 I have version 2.20 and with that version it is recommended to use firmware 9.0.1

---

