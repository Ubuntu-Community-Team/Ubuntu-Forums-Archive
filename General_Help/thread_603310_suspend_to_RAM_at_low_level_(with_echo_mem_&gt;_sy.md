---
title: "suspend to RAM at low level (with echo mem &gt; /sys/power/state) do not work"
date: 2007-11-05
forum: General Help
---

### Post by grof on 2007-11-05
I tried suspend to RAM with Kubuntu 7.10, but the system do not want make a real S3 state. It stuck somewhere in "middle state" where hard disk are turned off, but fans, monitor and power supply still working.

This problem is something newest in the Kubuntu 7.10. On old Kubuntu 7.04 (with older kernel) suspend to RAM works perfectly on the same hardware.

Exactly the same things happened on OpenSuse 10.3 (and in OpenSuse 10.2 it works perfectly).

I think that must be some kernel bug or similiar.

On both system I tried suspend to ram with init 1 runlevel, with minimal modules loaded in and with terminal command:

```
echo mem > /sys/power/state
```

My hardware is:
Desktop PC
Asus A8N SLi Deluxe mobo
AMD Athlon X64 3500+ Proc
ATI Radeon X300 Graph Card

Know anybody something about this??

thx.

---

