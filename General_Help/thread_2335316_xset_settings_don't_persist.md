---
title: "xset settings don't persist"
date: 2016-08-27
forum: General Help
---

### Post by os2 on 2016-08-27
If I set

```

xset r rate 200 50

```

it resets itself to 660 25 after about 30 seconds.

Has anyone seen this?

---

### Post by os2 on 2016-08-27
I thought this was a userspace issue with xserver/xset. Seems not to be the case.

I had a udev rule running which was triggering acpi events, and which was inadvertently resetting the keyboard thus causing xset to reset its repeat rate value.

---

