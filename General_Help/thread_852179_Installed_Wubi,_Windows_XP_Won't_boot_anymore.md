---
title: "Installed Wubi, Windows XP Won't boot anymore"
date: 2008-07-07
forum: General Help
---

### Post by bockman on 2008-07-07
Hello,

I installed Wubi, restarted into Ubuntu and was going fine. A few restarts later, and now Windows XP won't boot. After I select Windows XP, it brings me to another menu with various Safe Mode choices, last known good config, and start windows normally. No matter which option I choose, my laptop does a hard reset afterwards.

What can I do?

---

### Post by ago on 2008-07-07
Boot with a windows CD and run chkdsk /r from the rescue console. The above is usually the result of a hard reboot.

---

### Post by bockman on 2008-07-07
> **ago said:**
> Boot with a windows CD and run chkdsk /r from the rescue console. The above is usually the result of a hard reboot.

No errors. Ran with chkdsk and my laptop's built in low level hdd scan.

---

### Post by digitalggs on 2008-07-08
system service might be corrupted. withthe symptoms you describe (and no BSOD) sounds like lsass maybe. You can boot from windows CD and do a repair install (Fixes system files without purging your installed programs). You can also try a manual system restore (Long drawn out process that involves retrieving backed up regisry hives) if that dosent work. I dont have a link offhand but if you google 'Manual windows system restore' you should find the instructions, from MS website would be the best source. I think there is an intuitive step by step guide in thier KB ( I realize that 'Intuitive MS' may be an oxymoron)

---

