---
title: "BFD or Antidos not working on Ubuntu 6.06"
date: 2006-09-16
forum: General Help
---

### Post by Linux7 on 2006-09-16
Was curious if anyone has gotten BFD to work on Ubuntu 5 or 6?  APF seems to be working fine after installing and then running /sbin/iptables -L -n

BFD installs ok and cron does execute it but no blocking of any offending ip's is happening (they are happening).  /var/log/bfd_log has nothing in it at all and no e-mails have been received saying any logging is being blocked.

I also tried un-installing BFD and turned on APF's antidos but no logging either.

Any suggestions as to how I can narrow this down?  This is a Plesk 8 server.

Thanks...

---

