---
title: "Lubuntu / win 10 dual boot fail"
date: 2015-12-05
forum: General Help
---

### Post by billathome65 on 2015-12-05
I was running windows7 as a dual boot with Lubuntu however windows7 became corrupted and it was easier to upgrade to windows10 I upgraded and when the system starts I get the windows10 and Lubuntu choice.

When I choose 10 it loads up no problem but when i chose Lubuntu it just goes to a reboot? any ideas for a fix to this as I now can't access the files I had 

Cheers Bill

---

### Post by oldfred on 2015-12-05
From Ubuntu live installer in live mode's terminal install Boot-Repair.
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Is Windows 7 was BIOS and Ubuntu was in sda5 logical partition, Windows is known to forget to include that partition when it rewrote partition table. It has done that for years on major updates where partition table gets rewritten. If that is the case data is still there an we just need to add an entry back into partition table with parted rescue or testdisk.

---

