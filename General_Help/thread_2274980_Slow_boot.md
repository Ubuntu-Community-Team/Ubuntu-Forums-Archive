---
title: "Slow boot"
date: 2015-04-23
forum: General Help
---

### Post by leobos2 on 2015-04-23
Hi guys,

I changed one of my hdd's into a /home so I could free up some space on my ssd. But ever since, my boot is horrifically slow. Even slower than the time I had my ubuntu install on the hdd itself.

It does give me a ahci pcc probe fail on bootup, does this have anything to do with it? Couldn't find any correlation between the two of them.


~Leo

---

### Post by dino99 on 2015-04-23
> **leobos2 said:**
> Hi guys,

I changed one of my hdd's into a /home so I could free up some space on my ssd. But ever since, my boot is horrifically slow. Even slower than the time I had my ubuntu install on the hdd itself.

It does give me a ahci pcc probe fail on bootup, does this have anything to do with it? Couldn't find any correlation between the two of them.


~Leo

'pcc probe' is mostly an info, not a warning/error, and only says that your hardware does not have that feature; nothing to worry there, its a new kernel fonction.

About the slowness, check syslog and compare the output of 'sudo blkid' to 'etc/fstab' they need to match

---

### Post by leobos2 on 2015-04-23
> **dino99 said:**
> 'pcc probe' is mostly an info, not a warning/error, and only says that your hardware does not have that feature; nothing to worry there, its a new kernel fonction.

About the slowness, check syslog and compare the output of 'sudo blkid' to 'etc/fstab' they need to match

Thanks, there was an outdated entry in the fstab. Boots a lot quicker now.

---

