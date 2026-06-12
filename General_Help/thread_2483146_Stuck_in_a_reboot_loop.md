---
title: "Stuck in a reboot loop"
date: 2023-01-21
forum: General Help
---

### Post by spykp on 2023-01-21
Hello everybody! Thank you for taking the time to read my thread.

Here's my story;
While playing a game of LoL (on Windows 10 Pro OS) my pc suddenly and out of the blue freezes and my screen goes brown.
Pc reboots and gets stuck in a reboot loop.
I check BIOS and everything looks normal, I never tweaked anything.
A friend of mine suggests testing RAM by switching slots and trying one by one, but the  result is always the same.
After a few reboots, OS automatically prompts me to repair/downgrade updates/ system recover (tried all of them, nothing worked).
In a moment of desperation I decide to format my SSD in hopes that it might just be corrupted files and drivers, and we decide to go with Ubuntu.
The format is successful and everything seems to be working fine, until the OS starts to boot again and then the rebooting starts again.
Now I get this message:

[    0.446637] mce: [Hardware Error]: CPU 10: Machine Check: 0 Bank 5: bea0000001000108
[    0.446641] mce: [Hardware Error]: TSC 0 ADDR ffffffc1071dc4 MISC d012000100000000 SYND 4d000000 IPID 500b000000000
[    0.446645] mce: [Hardware Error]: PROCESSOR 2:a20f10 TIME 1674309329 SOCKET 0 APIC 9 microcode a201016
/dev/nvme0n1p2: recovering journal
/dev/nvme0n1p2: clean, 173473/3049816 files, 4400061/121965056 blocks
[    3.024421] mtd device must be supplied (device name is empty)
[    3.336174] sd 8:0:0:0: [sdc] No Caching mode page found
[    3.336193] sd 8:0:0:0: [sdc] Assuming drive cache: write through
_


My Specs are as follows;
CPU:Ryzen 5600x
Motherboard: Asrock b450m Steel Series
RAM: Patriot Viper 3200 C16 16GB dual kit
GPU: AMD Asus Strix R7 370
PSU: Corsair CX 600

---

### Post by MAFoElffen on 2023-01-21
Does it run from the install media if you select "try"?

From a Live Image Environment USB install media, please run the [UbuntuForums 'system-info' ]("https://github.com/UbuntuForums/system-info")script to provide information on your system...

From your errors... I am thinking maybe memory or your NVMe storage... You might try to reseat your NVMe drive beforehand...

---

