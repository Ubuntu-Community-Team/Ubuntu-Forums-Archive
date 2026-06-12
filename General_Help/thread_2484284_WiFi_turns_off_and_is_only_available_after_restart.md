---
title: "WiFi turns off and is only available after restart"
date: 2023-02-22
forum: General Help
---

### Post by fredaburg on 2023-02-22
The title already says it. I'm new to Ubuntu and have a HP notebook. 

Where can I find error logs, so that I can paste them here? It often happens, that WiFi suddenly turns off, and I can't search for new WiFi networks in my area. Reboot helps, but thats annoying.

Thanks,
Freda

---

### Post by MAFoElffen on 2023-02-22
To see the network statistics including errors:
```

grep . /proc/net/dev

```
To see what the wireless driver did in the system logs
```

sudo dmesg | grep $(sudo lshw -C network | grep -a11 'Wireless' | grep 'configuration:' | awk '{print $3}' | grep -v 'broadcast' | sed 's/driver\=//g' )

```

---

