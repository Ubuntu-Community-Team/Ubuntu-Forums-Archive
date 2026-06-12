---
title: "Failure to read sector when booting"
date: 2017-09-24
forum: General Help
---

### Post by cliffmitchell on 2017-09-24
I have a dual boot system: Ubuntu 16.04 and Windows 10.

When booting to Ubuntu I just started getting ‘error: failure to read sector 0xaf3c0 from ‘hd0’.
Press any key to continue…

Nothing happens when I press enter. 

I can boot successfully by selecting: 'Advanced options for Ubuntu' from the boot menu then 
'Ubuntu, with Linux 4.4.0-93-generic (recovery mode)' then selecting the 'Resume normal boot' option.
I can then log in and access Ubuntu as normal (but with reduced graphics options).

My question is, how can I recover from the bad sector error without completely restoring everything.
I have tried boot-repair but that didn’t help. Many thanks.

---

### Post by deadflowr on 2017-09-24
*Thread moved to **General Help**.*

---

### Post by oldos2er on 2017-09-24
Information about your hard disk(s) would help. SSD or "regular"? If you're using a regular mechanical hard disk, have you run SMART on it? If the disk is failing because of numerous bad sectors, the only solution is to replace it.

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

