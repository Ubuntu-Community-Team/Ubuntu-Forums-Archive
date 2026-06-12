---
title: "How do I make PowerTOP settings stick?"
date: 2015-03-19
forum: General Help
---

### Post by warren3 on 2015-03-19
Hi.

I am trying to make PowerTOP settings stick.  I have tried adding [I]

echo 'min_power' > '/sys/class/scsi_host/host2/link_power_management_policy';[/I] 

to my rc.local file but when I reboot and check PowerTOP it lists this as being 'bad', so its not working.

What am I doing wrong?

---

