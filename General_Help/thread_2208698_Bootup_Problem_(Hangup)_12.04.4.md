---
title: "Bootup Problem (Hangup) 12.04.4"
date: 2014-03-01
forum: General Help
---

### Post by jdr2 on 2014-03-01
Here is the problematic lines in dmesg log:

```
[Sat Mar  1 14:54:45 2014] HDMI: invalid ELD data byte 0
[Sat Mar  1 14:55:14 2014] type=1400 audit(1393703715.096:72): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=2488 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0

```
Information on my Video Card:
```
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde XT [Radeon HD 7770 GHz Edition]



```

Any Idea how to solve this? Thanks

---

