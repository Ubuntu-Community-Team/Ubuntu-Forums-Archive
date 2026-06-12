---
title: "Can't connect with Samba"
date: 2007-01-25
forum: General Help
---

### Post by meheheh on 2007-01-25
Hi,

I have a system running Ubuntu 6.06.1 Server Edition. After I moved it once and changed the IP address, I can't access it via samba with any system (Ubuntu, OSX, WinXP.) Any advice? SSH runs fine and as far as I know everything else is fine with the system.

thanks in advance

---

### Post by meheheh on 2007-01-25
NEVER MIND! I fixed it. Since my computers were getting IPs via static DHCP on my DD-WRT equipped WRT54G those IPs were on the allowed list. When I set static DHCP on the new pfSense firewalling system I didn't use the same IPs. Changing those in the allowed to access part of smb.conf fixed everything.

---

