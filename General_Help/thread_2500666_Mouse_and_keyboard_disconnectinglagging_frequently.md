---
title: "Mouse and keyboard disconnecting/lagging frequently."
date: 2024-09-08
forum: General Help
---

### Post by Anton_Hristov on 2024-09-08
Dear Ubuntu Community,

I've gone back to Ubuntu after a few year break and am having issues with my peripherals. My keyboard and mouse freeze for 3-4 second every few minutes.

After noticing the issue, I ran 

```
journalctl --no-pager -b -p warning
```

The logs were:
```
Sep 08 22:14:58 ant kernel: kauditd_printk_skb: 1 callbacks suppressed
Sep 08 22:14:58 ant acpid[820]: input device has been disconnected, fd 7
Sep 08 22:14:58 ant acpid[820]: input device has been disconnected, fd 8
Sep 08 22:14:58 ant acpid[820]: input device has been disconnected, fd 9
```

it seems like my input devices get disconnected and reconnected... Any ideas how to try to fix this... It's very annoying.

---

### Post by Autodave on 2024-09-09
Are you using any USB hubs?  If so, disconnect them and only connect your keyboard and mouse and see what happens.  I have several USB hubs here, both powered and non-powered.....that do exactly what you are describing.

---

