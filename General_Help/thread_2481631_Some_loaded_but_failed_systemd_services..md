---
title: "Some loaded but failed systemd services."
date: 2022-12-05
forum: General Help
---

### Post by zhaohscas on 2022-12-05
I'm currently using Ubuntu 22.10, as shown below:

```
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.10
Release:	22.10
Codename:	kinetic

```

I noticed the following failed systemd services:

```
$ systemctl --failed
  UNIT                                 LOAD   ACTIVE SUB    DESCRIPTION                              
&#9679; casper-md5check.service              loaded failed failed casper-md5check Verify Live ISO checksums
&#9679; systemd-networkd-wait-online.service loaded failed failed Wait for Network to be Configured

LOAD   = Reflects whether the unit definition was properly loaded.
ACTIVE = The high-level unit activation state, i.e. generalization of SUB.
SUB    = The low-level unit activation state, values depend on unit type.
2 loaded units listed.

```

Do you have any suggestions to solve these problems

Regards,
Zhao

---

