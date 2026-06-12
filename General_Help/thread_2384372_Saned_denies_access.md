---
title: "Saned denies access"
date: 2018-02-06
forum: General Help
---

### Post by burkina76 on 2018-02-06
Hi,

I followed the instructions in this tutorial

[https://help.ubuntu.com/community/SaneDaemonTutorial?action=show&redirect=sane.d+tutorial](https://help.ubuntu.com/community/SaneDaemonTutorial?action=show&redirect=sane.d+tutorial)

to set up a network scanner.

Everything should be set as needed. However, when I open xsane on a client PC (I tried more than one client, with the same result), the host saned denies access:

```
Feb  6 14:29:56 xxxxxxx systemd[1]: Started Scanner Service (xxx.xxx.xx.xxx:46488).
Feb  6 14:29:56 xxxxxxx saned[5122]: saned (AF-indep+IPv6) from sane-backends 1.0.26git starting up
Feb  6 14:29:56 xxxxxxx saned[5122]: check_host: access by remote host: localhost
Feb  6 14:29:56 xxxxxxx saned[5122]: init: access by host localhost denied
Feb  6 14:29:56 xxxxxxx saned[5122]: saned exiting
```

I'm puzzled here by the fact that the access request comes from 'localhost' instead of the client IP/name. If I indeed include localhost in the allowed IPs, the log changes into:

```
check_host: access by remote host: localhost
init: bad status=22 or procnum=6350304
```

I tried several things (add saned to lp and saned groups, modify saned@.service, define permission rules for saned), but nothing changes. Of course, the scanner works locally on the host. If, however, I add localhost both in saned.conf and in net.conf, I can connect to the scanner only locally, no second 'localhost' copy is detected by xsane (as mentioned in the tutorial for troubleshooting).

Do you have any idea?

Thanks,
Stefano

---

### Post by burkina76 on 2018-03-12
After several efforts, it seems that the solution came by upgrading sane-backends from 1.0.26git to 1.0.27git.

---

