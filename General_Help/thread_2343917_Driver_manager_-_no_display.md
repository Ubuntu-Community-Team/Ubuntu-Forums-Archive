---
title: "Driver manager - no display ?"
date: 2016-11-20
forum: General Help
---

### Post by oygle on 2016-11-20
Driver manager in 16.04.1 doesn't work. It displays "Collecting information about your system" - that was 15 minutes ago.  lol

System Monitor shows **kcmshell5** as the process  ??

edit - found more info ..

```
kcmshell5 kcm_driver_manager
```

> libGL error: unable to load driver: nouveau_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: nouveau
No frame loaded
No frame loaded
No frame loaded
No frame loaded
No frame loaded
No frame loaded

Have had problems with the video/display since doing a fresh install of 16.04.1 - [https://ubuntuforums.org/showthread.php?t=2340444](https://ubuntuforums.org/showthread.php?t=2340444)

[https://bugs.launchpad.net/ubuntu/+source/libqapt/+bug/1530523](https://bugs.launchpad.net/ubuntu/+source/libqapt/+bug/1530523)

See attachment

---

