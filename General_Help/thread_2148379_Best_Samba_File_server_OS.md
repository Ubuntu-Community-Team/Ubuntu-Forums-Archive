---
title: "Best Samba File server OS?"
date: 2013-05-25
forum: General Help
---

### Post by owemeacent on 2013-05-25
I have had intermediate experience with linux and I want to make my vista computer a server that runs linux. It has 4gb of RAM, and an AMD Phenom II 2.3 triple core. I just want a simple Samba file server that can store documents and videos that is simple to set up and very stable and rarely needs rebooting. I can't figure out which Linux distro is best for my needs, I've narrowed it down to CentOS, Ubuntu, Debian, and SUSE enterprise. SO if you guys could help me find the best stable server os, that'll be great:D

---

### Post by lethall1 on 2013-05-25
ubuntu server 12.04 LTS + ext4 + samba (works greate) + NAS for backups + ethernet bonding (if you have more then 1 pc in network)+ iptables + fail2ban (if you would you auth in samba)
Hm ) i have a lot of such servers, works just greate, without rebooting )
FreeBSD is greate too and stable (and BSD base)
recently i install debian (if you plan to update you soft and os, debian is more stable)

---

### Post by 2F4U on 2013-05-25
Basically all of the distributions you mention will do the job. SLES (SUSE Linux Enterprise Server) is a commercial product. So, if you need commercial support and are willing to pay for it, SLES is one alternative (RHEL being another one). CentOS (and Scientific Linux) are based off RHEL (Red Hat Enterprise Linux). Now it depends with which distribution you are more familiar (package managment etc.).

---

### Post by Cheesemill on 2013-05-25
If this is only going to be used for a NAS box then I would use FreeNAS, it's designed for exactly that purpose.

[http://www.freenas.org/](http://www.freenas.org/)

---

### Post by HiImTye on 2013-05-25
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
as 2F4U said, the package manager is going to be the main difference in the distros, as the other tools will be more or less the same for each. Ubuntu takes a lot of the guess work out, but also can be a pain to navigate all of the extra layers that result from it.

---

### Post by prodigy_ on 2013-05-25
> **owemeacent said:**
> I've narrowed it down to CentOS, Ubuntu, Debian, and SUSE enterprise.
Any particular reason for excluding Gentoo? It's a rolling release, 100% configurable distro that is ideal for pure server installations.

---

### Post by owemeacent on 2013-05-25
But is Gentoo easy to install and configure? I've used Arch Linux a lot, so is Gentoo a bit like Arch?

---

