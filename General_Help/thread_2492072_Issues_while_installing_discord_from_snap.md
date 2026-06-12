---
title: "Issues while installing discord from snap"
date: 2023-10-29
forum: General Help
---

### Post by kingpenguin on 2023-10-29
**Error:**

```
sudo snap install discord
error: cannot perform the following tasks:
- Fetch and check assertions for snap "discord" (160)
  (Get "https://api.snapcraft.io/v2/assertions/snap-revision/JnfG8judXTzZIXq5_cptCwZBQ3S_WGiJIcspY5_ozmCYdF6L49CLzERf-BUkdhLK?max-format=0":
  net/http: request canceled while waiting for connection (Client.Timeout exceeded while awaiting headers))
- Download snap "gnome-42-2204" (141) from channel "stable"
  (read tcp 192.168.1.5:59068->91.189.91.43:443: read: connection timed out)
- Fetch and check assertions for snap "gtk-common-themes" (1535)
  (Get "https://api.snapcraft.io/v2/assertions/snap-revision/62rRwo_VHrOdajhLlnNTqUJ8gfWoZZNSFWhxn2AszCKyUAD0d8guxddMFeW5LVKP?max-format=0":
  net/http: request canceled while waiting for connection (Client.Timeout exceeded while awaiting headers))




```**What I am doing:** When I attempt to run sudo snap install discord, I encounter the error mentioned above. It's worth noting that I also encountered this error during a previous attempt without making any changes to my system, indicating that the error message changed:

```
lookup api.snapcraft.io: Temporary failure in name resolution

```


I took a look at [https://status.snapcraft.io/](https://status.snapcraft.io/) and it is making me believe that the system is up but it might be on my end. 
I am able to run dig api.snapcraft.io and it gives me 4 ip address's so I am not sure why I was getting the temporary failure in name resolution. If you have any idea on how to troubleshoot this please let me know.

---

### Post by kingpenguin on 2023-10-29
It just seemed that I needed a reboot. I am not exactly sure why but after a reboot I was able to install discord.

---

