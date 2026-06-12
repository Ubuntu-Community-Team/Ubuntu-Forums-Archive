---
title: "Can't run programs installed via snap"
date: 2017-12-21
forum: General Help
---

### Post by fmattheus on 2017-12-21
I have some programs that I have previously installed via snap, that used to work, but now I get a lovely "command not found" when trying to run them.  See the following output as an example.

```

$ snap list
Name        Version      Rev   Developer     Notes
core        16-2.29.4.2  3604  canonical     core
ddgr        1.1          3     snapcrafters  -
googler     3.4          11    snapcrafters  -
multipass   2017.2.2     37    saviq         classic
pulsemixer  1.3.0        1     snapcrafters  -
$ ddgr
ddgr: command not found
$ pulsemixer
pulsemixer: command not found

```

In the logfiles, the relevant lines that I could find are the following:
```

/var/log/syslog:Dec 21 09:24:36 hostname snapd[5528]: 2017/12/21 09:24:36.284580 helpers.go:202: cannot connect plug "network-bind" from snap "core", no such plug
/var/log/syslog:Dec 21 09:25:20 hostname snapd[2214]: 2017/12/21 09:25:20.611923 stateengine.go:98: state ensure error: Get https://api.snapcraft.io/api/v1/snaps/sections: dial tcp: lookup api.snapcraft.io: Temporary failure in name resolution
/var/log/syslog:Dec 21 09:25:29 hostname multipass.multipassd[2788]: QIODevice::write (QFile, "/var/snap/multipass/common/cache/multipassd/vault/multipassd-image-records.json"): device not open

```

Anyone have an idea of what happened or how I can fix it?

EDIT: I'm running 16.04

---

