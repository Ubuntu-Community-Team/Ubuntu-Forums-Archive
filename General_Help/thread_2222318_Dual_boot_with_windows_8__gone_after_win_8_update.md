---
title: "Dual boot with windows 8  gone after win 8 update"
date: 2014-05-06
forum: General Help
---

### Post by strider3700 on 2014-05-06
last Friday I shutdown my win8 laptop and rebooted into linux.  I spent all weekend in linux then powered down this morning. On reboot the boot loader came up and I told it to go into windows 8 UEFI.  The very first thing that happened was windows reported that it had an update to install and needed to reboot.   I did the reboot and spent the day in windows.  Tonight I went to reboot into linux and the machine instantly boots back into windows.   I'm not sure if the bootloader become corrupted or was overwritten.    

How can I reinstall or recover the bootloader so that I can get back into linux?

---

### Post by oldfred on 2014-05-06
Had you run Boot-Repairs buggy fix? Best not to unless that is the only choice. Only for those systems where vendor modifies UEFI to only boot Windows.

Also Windows automatically makes itself first in UEFI on any Windows maintenance.
And it may  have turned secure boot back on and/or fast boot. Check that both are off.

Does UEFI menu still show an ubuntu entry and was that what you used to boot.

May be best to see details. Also what model computer.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

