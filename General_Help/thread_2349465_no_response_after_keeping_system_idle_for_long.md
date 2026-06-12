---
title: "no response after keeping system idle for long"
date: 2017-01-15
forum: General Help
---

### Post by kranthi.t2000 on 2017-01-15
Hi,
I am using a Lenovo Ideapad 300 15ISK. I installed the latest Lubuntu Flavor 16.10 version.
Whenever I keep the system Idle for long, the monitor switches off and doesn't switch on again. In case it does switch on, no application works properly; including the terminal. the dmesg shows the following error which is the only one marked red:
```

platform MSFT0101:00: failed to claim resource 1
acpi MSFT0101:00: platform device creation failed: -16

```
How do I find out which component is causing the problem? any commands that I should try?

---

### Post by HermanAB on 2017-01-15
There was a problem with a recent kernel that would 'die' with all processor cores idled.  So try upgrading the kernel.

---

### Post by kranthi.t2000 on 2017-01-15
@HermanAB How do I know whether my kernel already is patched from that bug? My kernel version is 4.8.0-34. Is it already patched?

Also, the same problem arises for windows too. For W10, the system crashes and reboots if I keep the system Idle for long.

---

