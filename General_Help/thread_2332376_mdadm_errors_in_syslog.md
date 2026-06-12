---
title: "mdadm errors in syslog"
date: 2016-07-31
forum: General Help
---

### Post by greytony on 2016-07-31
Hi,

I am receiving the following errors in syslog:

Process '/sbin/mdadm --incremental /dev/sdb1 --offroot' failed with exit code 1.

I get the same error for sdc1 and sdd1.

However, my raid5 array is mounting and working properly.

I was wondering what the problem is?

my /etc/mdadm/mdadm.conf contents:

```

CREATE owner=root group=disk mode=0660 auto=yes
HOMEHOST <system>
MAILADDR root
ARRAY /dev/md/0 metdata=1.2 UUID=73a3720a:da34a4d1:62649d74:63786e4a name=argon:0

```

Any help would be much appreciated.

---

