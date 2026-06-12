---
title: "Tracking Internet Usage?"
date: 2016-02-20
forum: General Help
---

### Post by Terone on 2016-02-20
So I left my computer on in the night accidentally (Kubuntu 15.10) connected to the internet (was exhausted) and when I woke up, my internet usage was blown out of proportion, which lead to a hefty bill.

There was nothing open at the time.

Is there anyway to track who or what program is causing this?

---

### Post by sandyd on 2016-02-21
I would either try either the iftop or iptraf-ng utility. Both can show in real-time which ports are using the most traffic.

Setting up iptraf:
```

sudo apt-get install iptraf-ng

```

From here, thare are a few options.

To view details (mainly byte/packet count + sending/receiving ip and port)
sudo iptraf-ng -i *interface*

To view (TCP/UDP) info```

sudo iptraf-ng -s *interface*
```

Use 'S' to sort, sometimes it does not sort on it's own.

Setting up iftop:
```

sudo apt-get install iftop
sudo iftop -i *interface*
```
After the ports are identified, you can either use netstat or lsof to identify what application is using the traffic.

---

