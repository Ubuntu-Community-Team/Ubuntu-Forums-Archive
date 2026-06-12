---
title: "Canonical Livepatch not work"
date: 2017-02-24
forum: General Help
---

### Post by sensez on 2017-02-24
My system version: ubuntu 16.04.2 LTS
Kernel version: Linux tree 4.4.0-64-generic #85-Ubuntu SMP Mon Feb 20 11:50:30 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
I install the snapd, version is 2.22.3

I had get a kernel patching key from [https://auth.livepatch.canonical.com/?user_type=ubuntu-user](https://auth.livepatch.canonical.com/?user_type=ubuntu-user). Then I install canonical-livepatch but got some errorr:
```

$ sudo snap install canonical-livepatch
$ sudo canonical-livepatch enable [key]

Connection to the daemon failed: Put http://127.0.0.1/enable?auth-token=[key]: dial unix /var/snap/canonical-livepatch/17/livepatchd-priv.sock: connect: no such file or directory

```

There are some error in /var/log/syslog too:
```

Feb 25 00:37:03 tree canonical-livepatch[7149]: cmd.go:111: DEBUG: restarting into "/snap/core/current/usr/bin/snap"
Feb 25 00:37:03 tree kernel: [22652.049941] audit: type=1400 audit(1487954223.310:64): apparmor="DENIED" operation="capable" profile="snap.canonical-livepatch.canonical-livepatch" pid=7149 comm="canonical-livep" capability=1  capname="dac_override"
Feb 25 00:37:03 tree kernel: [22652.049952] audit: type=1400 audit(1487954223.310:65): apparmor="DENIED" operation="capable" profile="snap.canonical-livepatch.canonical-livepatch" pid=7149 comm="canonical-livep" capability=2  capname="dac_read_search"

```

Could someone tell me how to get it work? Thanks a lot!

---

### Post by #&amp;thj^% on 2017-02-24
This has been problematic for some others also.
Try this to see if it works:
```
sudo /snap/bin/canonical-livepatch enable ID
```

---

### Post by sensez on 2017-02-25
> **1fallen said:**
> This has been problematic for some others also.
Try this to see if it works:
```
sudo /snap/bin/canonical-livepatch enable ID
```
It works! Thanks you very much!

---

