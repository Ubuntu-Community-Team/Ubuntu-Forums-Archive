---
title: "Slow boot, Kinit: name_to_dev_t"
date: 2007-08-06
forum: General Help
---

### Post by Zorael on 2007-08-06
My Ubuntu system is very slow to boot.

If I ALT-F1 out of the splash screen I see it waiting for up to ~40 seconds at:
```
Loading, pease wait...
*<long pause>*
Kinit: name_to_dev_t(/dev/disk/by-uuid/<the uuid of my swap partition>)= sda6(8,6)
kinit: No resume image, doing normal boot...
```

It's pretty much the same issue as the one described at [https://bugs.launchpad.net/ubuntu/+bug/103148](https://bugs.launchpad.net/ubuntu/+bug/103148). (And doh, forgot to paste it in the special launchpad box when I posted this)

Everything else works, no issues once past that pause. Any way to manually tell it to look at /dev/sda6 to begin with instead of looking it up by the uuid?

---

