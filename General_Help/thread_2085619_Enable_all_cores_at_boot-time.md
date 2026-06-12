---
title: "Enable all cores at boot-time"
date: 2012-11-18
forum: General Help
---

### Post by editheraven on 2012-11-18
I was doing a general check in dmesg for errors and i saw something that intrigued me

"[25010.556730] Disabling non-boot CPUs ...
[25010.660016] CPU 1 is now offline
[25010.764009] CPU 2 is now offline"

This assumes that at boot-time (i have a tripple core amd) the 2nd and 3rd core is down? And if so, enabeling them would make boot process faster (i am asking mainly not for my desktop but for laptop which boots kinda slow).

Thanx.

---

### Post by idoitprone on 2012-11-18
> **editheraven said:**
> I was doing a general check in dmesg for errors and i saw something that intrigued me

"[25010.556730] Disabling non-boot CPUs ...
[25010.660016] CPU 1 is now offline
[25010.764009] CPU 2 is now offline"

This assumes that at boot-time (i have a tripple core amd) the 2nd and 3rd core is down? And if so, enabeling them would make boot process faster (i am asking mainly not for my desktop but for laptop which boots kinda slow).

Thanx.

25010sec / 60 min/sec= 416 min
I agree 416 minutes is too long to be a proper boot time

next time use

```
dmesg | head -n 1000
```

those messages are mundane core sleep messages

---

### Post by Linuxisfast on 2012-11-19
> **idoitprone said:**
> 25010sec / 60 min/sec= 416 min
I agree 416 minutes is too long to be a proper boot time

next time use

```
dmesg | head -n 1000
```

those messages are mundane core sleep messages

I remember there used to be a concurrent command to be passed on to GRUB, wonder if thats been depreciated, that command would use all the CPU's for boot process.

---

### Post by Yellow Pasque on 2012-11-19
I'm guessing you put your system in suspend/sleep/hibernate when those messages were logged.

---

### Post by idoitprone on 2012-11-19
> **Linuxisfast said:**
> I remember there used to be a concurrent command to be passed on to GRUB, wonder if thats been depreciated, that command would use all the CPU's for boot process.

upstart for ubuntu does uses all cores for boot

Booting is generally io bound, so it wont make much difference if all core are active.

---

### Post by dcstar on 2012-11-19
> **editheraven said:**
> I was doing a general check in dmesg for errors and i saw something that intrigued me

"[25010.556730] Disabling non-boot CPUs ...
[25010.660016] CPU 1 is now offline
[25010.764009] CPU 2 is now offline"

This assumes that at boot-time (i have a tripple core amd) the 2nd and 3rd core is down?

No, as the other poster told you these time stamps are hours after boot time, they are probably normal power saving messages as the system turns off unneeded CPUs.

"Boot time" is the first few tens of seconds of the dmesg file.

---

