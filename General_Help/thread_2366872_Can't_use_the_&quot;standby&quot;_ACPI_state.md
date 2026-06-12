---
title: "Can't use the &quot;standby&quot; ACPI state"
date: 2017-07-22
forum: General Help
---

### Post by togop2 on 2017-07-22
My computer doesn't support the S3 suspend to ram ACPI state, so I'm trying to use S1 "standby". However, it doesn't seem to be available:
$ cat /sys/power/state 
freeze disk

How can I find out why? Hardware should support it. Is there some way to enable it?

---

