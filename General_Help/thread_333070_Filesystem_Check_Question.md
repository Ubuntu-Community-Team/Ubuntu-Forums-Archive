---
title: "Filesystem Check Question"
date: 2007-01-06
forum: General Help
---

### Post by tonester on 2007-01-06
I am running Dapper Drake, and all linux filesystems are checked at every 30 bootups.

If I issue the command:

sudo shutdown -rF now

is the filesystem check "counter" reset at 30?

Just curious...

TIA

---

### Post by dcstar on 2007-01-06
> **tonester said:**
> I am running Dapper Drake, and all linux filesystems are checked at every 30 bootups.

If I issue the command:

sudo shutdown -rF now

is the filesystem check "counter" reset at 30?

Just curious...

TIA

AFAIK the filesystem check is "N" period or "N" mounts since the last check, so the answer should be yes.

**man tune2fs** if you want more info on changing the default 30 setting.

---

### Post by tonester on 2007-01-06
OK - Thanks for the reply  :)

---

