---
title: "Blinking cursor after GRUB (sometimes)"
date: 2012-11-18
forum: General Help
---

### Post by Xtyn on 2012-11-18
I've seen this issue on two different PCs with Lubuntu 12.10. After GRUB, there is a blinking cursor and nothing else, I have to force a reboot and after that it works fine. This rarely happens, but it is annoying.

Moreover, I've seen that I have the same problem on my PC with Debian, I've seen it freezing while loading the kernel (just after GRUB), but if I force a reboot, it works fine.

My problem is on an Intel d510mo motherboard, nothing fancy. As far as I can remember, older versions of Lubuntu did not have this issue. I think Lubuntu 11.10 worked fine. I've seen this same problem on an Acer emachines notebook. 

How can I find out what the problem is?

---

### Post by greatsirkain on 2012-11-18
yup, sometimes happens to me if I don't press f12 for the boot menu at boot and select where to boot from

---

### Post by Xtyn on 2012-11-18
> **greatsirkain said:**
> yup, sometimes happens to me if I don't press f12 for the boot menu at boot and select where to boot from
It should know where to boot from. Plus, why does it know most of the times and not every time?

---

### Post by raja.genupula on 2012-11-18
Hi
          To understand your problem in a better way , we need your log .

open your terminal and type as 

```
dmesg
```

and paste here between the code tags .

---

### Post by Xtyn on 2012-11-18
> **raja.genupula said:**
> Hi
          To understand your problem in a better way , we need your log .
It's a bit long, so I've put it here, if you don't mind:
[http://paste.ubuntu.com/1368401/](http://paste.ubuntu.com/1368401/)

---

