---
title: "lxd.service failed on boot"
date: 2019-03-12
forum: General Help
---

### Post by masked-bit on 2019-03-12
We recently noticed that **lxd.service** failed on boot.

[LIST=1]
[*]How critical is the lxd service to Ubuntu 16.04 server? 
[*]**Can we disable it and expect OS stability? ** I am talking about the standard 16.04 distro, not including any added packages. 
[*]If lxd/lxc are required, then we will need to juggle systemd services and dependencies to accomodate them with aufs (another unified file system).  **Any guidance here would be most appreciated.** 
[/LIST]
 
System Particulars:

[LIST]
[*]Real time embedded system 
[*]Ubuntu 16.04 Server with xenomai kernel 
[*]*uname -a* yields: Linux 4.1.18-xenomai-2.6.5 #9 SMP i686 i686 i686 GNU/Linux 
[/LIST]

---

