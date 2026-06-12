---
title: "nm-applet hangs on certain dhcp networks"
date: 2008-02-27
forum: General Help
---

### Post by komputes on 2008-02-27
For some reason nm-applet 0.6.5 does not get an address automatically on all networks. For some reason I need to run

```
sudo dhclient
```

to get an IP address through DHCP. At that point, the IP in ifconfig is correct (192.168.x.x) but in nm-applet the "Connection information" is zeroed out (0.0.0.0).

Any ideas why this needs to be done on certain networks and not on others. Is this possibly a security risk?

---

