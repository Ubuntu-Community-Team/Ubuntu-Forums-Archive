---
title: "transmission-daemon cannot open the web interface?"
date: 2015-01-06
forum: General Help
---

### Post by shamsat on 2015-01-06
In ubuntu 14.10 want to open [http://127.0.0.1:9091](http://127.0.0.1:9091) the transsmission-daemon web interface get this error:
```

403: Forbidden

Unauthorized IP Address.

Either disable the IP address whitelist or add your address to it.

If you're editing settings.json, see the 'rpc-whitelist' and 'rpc-whitelist-enabled' entries.

If you're still using ACLs, use a whitelist instead. See the transmission-daemon manpage for detail

```
the rpc-whitelist-enabled is set to false in the settings.json:

```

"rpc-whitelist": "127.0.0.1, 127.0.1.1, 192.168.1.*, 10.42.0.*",
    "rpc-whitelist-enabled": false,

```

---

