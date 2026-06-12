---
title: "reseting iptables to default"
date: 2007-07-23
forum: General Help
---

### Post by nvteighen on 2007-07-23
Hi, I've tried Firestarter; it really didn't convince me and I've removed it, but iptables was modified by it. Is there a way to reset iptables to the exact default settings from Ubuntu? I haven't opened any port, but I want to be sure... Or may I leave it?

Thanks in advance!

---

### Post by trak87 on 2007-07-23
The default settings of iptables are to not block anything. If you've removed Firestarter and rebooted you will return to the non-blocking state and you don't need to to anything. Otherwise you can do this:

```
sudo iptables -F
```

---

### Post by nvteighen on 2007-07-23
I've rebooted and iptables is set to default. Thanks!

Now, I have always understood the default state is secure and that firestarter should be use only if I'd like to open ports, or not? (Please don't tell me I must get firestarter again! #-o) According to Shields Up, all ports are shown as stealth. I don't use servers and my internet activity is just web and email... shouldn't be enough to me to stay with the default iptables?

---

