---
title: "Dell firmware won't update"
date: 2023-05-24
forum: General Help
---

### Post by Music_Guy on 2023-05-24
I'm running Ubuntu Studio 22.04 (fresh install) on a Dell desktop.  For the last month or so I've seen a notification for a Dell firmware update in the updater app.  I've clicked "update"; however the firmware will not update.  I have not seen any error messages.  When I run ```
fwupdmgr
``` I see the message:

(fwupdmgr:101182): dconf-WARNING **: 12:55:45.147: unable to open file '/etc/dconf/db/site': Failed to open file “/etc/dconf/db/site”: open() failed: No such file or directory; expect degraded performance.

Running ```
fwupdmgr get-devices
``` I get:


&#9500;&#9472;CT2000MX500SSD1:
&#9474;     Device ID:          5dbeb140337f610d54913c0f43d15fdaa0eafb51
&#9474;     Summary:            ATA drive
&#9474;     Current version:    M3CR045
&#9474;     Vendor:             Micron (ATA:0x1344, OUI:00a075)
&#9474;     GUIDs:              046771bf-4f0c-556f-9c2b-08fe18be91dc
&#9474;                         b970437d-4c27-5eb2-a55a-571b36af5423
&#9474;                         86678006-2dc3-5d34-8e82-21d5735bbcad
&#9474;     Device Flags:       • Internal device
&#9474;                         • Updatable
&#9474;                         • System requires external power source
&#9474;                         • Needs a reboot after installation
&#9474;                         • Device is usable for the duration of the update
&#9474;   
&#9500;&#9472;PM981 NVMe Samsung 256GB:
&#9474;     Device ID:          03281da317dccd2b18de2bd1cc70a782df40ed7e
&#9474;     Summary:            NVM Express solid state drive
&#9474;     Current version:    EXD72D1Q
&#9474;     Vendor:             Samsung (NVME:0x144D)
&#9474;     GUIDs:              0b4d773a-7ac3-58c1-a541-e22ef1cdfe02
&#9474;                         c9d531ea-ee7d-5562-8def-c64d0d144813
&#9474;                         6e54c992-d302-59ab-b454-2d26ddd63e6d
&#9474;                         47335265-a509-51f7-841e-1c94911af66b
&#9474;                         848a0a55-2a1e-5a3f-a9ea-2f11335d0527
&#9474;     Device Flags:       • Internal device
&#9474;                         • Updatable
&#9474;                         • System requires external power source
&#9474;                         • Needs a reboot after installation
&#9474;                         • Device is usable for the duration of the update
&#9474;                         • Signed Payload
&#9474;   
&#9500;&#9472;System Firmware:
&#9474; &#9474;   Device ID:          a45df35ac0e948ee180fe216a5f703f32dda163f
&#9474; &#9474;   Summary:            UEFI ESRT device
&#9474; &#9474;   Current version:    2.19.0
&#9474; &#9474;   Minimum Version:    2.19.0
&#9474; &#9474;   Vendor:             Dell (DMI:Dell Inc.)
&#9474; &#9474;   Update State:       Success
&#9474; &#9474;   GUIDs:              c0745fac-f5a5-46c9-b716-3cc5781e876e
&#9474; &#9474;                       230c8b18-8d9b-53ec-838b-6cfc0383493a
&#9474; &#9474;   Device Flags:       • Internal device
&#9474; &#9474;                       • Updatable
&#9474; &#9474;                       • System requires external power source
&#9474; &#9474;                       • Supported on remote server
&#9474; &#9474;                       • Needs a reboot after installation
&#9474; &#9474;                       • Cryptographic hash verification is available
&#9474; &#9474;                       • Device is usable for the duration of the update
&#9474; &#9474; 
&#9474; &#9492;&#9472;UEFI dbx:
&#9474;       Device ID:        362301da643102b9f38477387e2193e57abaa590
&#9474;       Summary:          UEFI revocation database
&#9474;       Current version:  275
&#9474;       Minimum Version:  275
&#9474;       Vendor:           UEFI:Linux Foundation
&#9474;       Install Duration: 1 second
&#9474;       GUIDs:            00fe3755-a4d8-5ef7-ba5f-47979fbb3423
&#9474;                         4a6cd2cb-8741-5257-9d1f-89a275dacca7
&#9474;                         c6682ade-b5ec-57c4-b687-676351208742
&#9474;                         f8ba2887-9411-5c36-9cee-88995bb39731
&#9474;       Device Flags:     • Internal device
&#9474;                         • Updatable
&#9474;                         • Needs a reboot after installation
&#9474;                         • Only version upgrades are allowed
&#9474;                         • Signed Payload
&#9474;     
&#9492;&#9472;TPM 2.0:
      Device ID:          a3487e128cf1413519bce8e9a1ab3f5981e61458
      Summary:            UEFI ESRT device
      Current version:    7.2.0.2
      Vendor:             Dell Inc. (PCI:0x1028)
      Update State:       Success
      GUIDs:              6ed025d4-7c75-59de-ab55-53191b2657e0
                          ff71992e-52f7-5eea-94ef-883e56e034c6
                          7d65b10b-bb24-552d-ade5-590b3b278188
                          6f5ddd3a-8339-5b2a-b9a6-cf3b92f6c86d
                          fe462d4a-e48f-5069-9172-47330fc5e838
      Device Flags:       • Internal device
                          • Updatable
                          • System requires external power source
                          • Needs a reboot after installation

I found a website that explains how to update the firmware ([https://linuxopsys.com/topics/update-firmware-on-ubuntu-using-fwupd](https://linuxopsys.com/topics/update-firmware-on-ubuntu-using-fwupd)).  

I am not familiar with this site.  Is this approach valid? I don't want to use this approach and screw up my computer.  If it's not a good way, can anyone suggest how to update the firmware?

---

### Post by MAFoElffen on 2023-05-24
Answered today, here: [https://askubuntu.com/questions/1469209/unable-to-install-dell-firmware-upgrade](https://askubuntu.com/questions/1469209/unable-to-install-dell-firmware-upgrade)

Note my comment which refers back to the original, full solution...

---

### Post by oldfred on 2023-05-24
More info:
[https://fwupd.org/](https://fwupd.org/)
[https://github.com/fwupd/fwupd](https://github.com/fwupd/fwupd)
[https://github.com/fwupd/fwupd/releases/tag/1.6.0](https://github.com/fwupd/fwupd/releases/tag/1.6.0)
Devices using LVFS for firmware updates
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)

Dell was one of the first major vendors to support UEFI update.
[https://www.phoronix.com/scan.php?page=news_item&px=Fwupd-1.4-Released](https://www.phoronix.com/scan.php?page=news_item&px=Fwupd-1.4-Released)
UEFI/BIOS updates brand model list  for Dell with (uefi >= 0.6.2 & dell >= 0.7.3) 

[https://www.phoronix.com/news/Fwupd-1.8.8-Released](https://www.phoronix.com/news/Fwupd-1.8.8-Released)

---

### Post by Music_Guy on 2023-05-24
I ran dconf update which installed the file .../site.  This got rid of the error message; however, the firmware still will not update.  Thanks for the suggestion - I just learned something new.

---

### Post by Music_Guy on 2023-05-24
Thanks oldfred.  Gonna take a little time to read and understand ...

---

