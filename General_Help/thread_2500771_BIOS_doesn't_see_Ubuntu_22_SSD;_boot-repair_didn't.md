---
title: "BIOS doesn't see Ubuntu 22 SSD; boot-repair didn't fix"
date: 2024-09-11
forum: General Help
---

### Post by bloodae on 2024-09-11
Hello! I plugged an ESP32 microcontroller board in my computer to perform a firmware upgrade on it, and while uploading, my MSI laptop shutdown. When I tried rebooting, it tried to boot on my 2nd SSD on Windows. When I checked the BIOS, the Ubuntu SSD didn't show up. I opened the laptop, swapped the two SSDs, and rebooted, but with the same result: the Windows SSD boots and the Ubuntu SSD doesn't show up in BIOS. I installed Ubuntu 22 live on a USB stick and followed the community guide for the recommended boot-repair. The SSD and all its partitions show up in "Disks" (including encrypted files), and when I right-click "Check filesystem" for the first 2 partitions (/boot and ??, respectively 531 MB and 1.8 GB), Disks shows no filesystem errors. The Ubuntu SSD still doesn't appear in BIOS.

Here's the pre-repair log: [https://paste.ubuntu.com/p/vKVrNj4BMm/](https://paste.ubuntu.com/p/vKVrNj4BMm/)
And here is the post-repair log: [https://paste.ubuntu.com/p/NjSjBmdPjG/](https://paste.ubuntu.com/p/NjSjBmdPjG/)

I'm not sure where to got from there. I figure a bad block repair might help, but I'm not familiar with that. Thanks for your help.

---

### Post by bloodae on 2024-09-11
Alright, so I read about NVRAM lock, and re-opened the laptop to unplug the RTS1 battery for 10 seconds, then rebooted to BIOS. I did not check these before, but the bios could see the 2 SSDs as PCIe devices, and then I went to boot options, and checked the BBS boot priority setting (or something like that). Turns out Windows was selected as #1, and Ubuntu was there as #2. So I swapped them and rebooted, and Ubuntu showed up. So, uh, thanks anyway, maybe that can help someone later.

---

