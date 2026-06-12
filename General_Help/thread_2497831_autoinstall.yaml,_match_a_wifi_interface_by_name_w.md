---
title: "autoinstall.yaml, match a wifi interface by name wildcard, 24.04"
date: 2024-05-19
forum: General Help
---

### Post by jds8086 on 2024-05-19
Is there any way to get similar functionality for WiFi interfaces as you can for hard wired ethernet modules via match: name: *wildcard*? I am trying to setup an automated install that will connect to a network regardless of the name of the wifi interface. I am away from this setup at the moment but my config was (or very close to) the following, and it gave an error which said fairly point blank that you cannot use match with wifis.

```
network:
    version: 2
    ethernets:
        all-en:
            match:
                name: "en*"
            dhcp4: true
    wifis:
        all-wl:
            match:
                name: "wl*"
            dhcp4: true
            access-points:
                "network_ssid_name":
                    password: "**********"

```

---

