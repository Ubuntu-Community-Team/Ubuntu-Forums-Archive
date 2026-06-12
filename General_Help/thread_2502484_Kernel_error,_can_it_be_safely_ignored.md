---
title: "Kernel error, can it be safely ignored?"
date: 2024-11-17
forum: General Help
---

### Post by wyattwhiteeagle on 2024-11-17
If this log message can safely be ignored, how do I have this message not be reported in logs or loggged with a less severe priority?


I have this error message in kernel log and syslog.
```
/var/log/syslog:2024-11-16T06:17:17.711069-05:00 wyatt-aspiree1532 kernel: warning: `ThreadPoolForeg' uses wireless extensions which will stop working for Wi-Fi 7 hardware; use nl80211
```


Another user had a similar message at an earlier date, here
[https://ubuntuforums.org/showthread.php?t=2486764](https://ubuntuforums.org/showthread.php?t=2486764)


There's a possible patch for this...
[https://patchwork.kernel.org/project/linux-wireless/patch/20230224135933.94104aeda1a0.Ie771c6a66d7d6c3cf67da5f3b0c66cea66fd514c@changeid/](https://patchwork.kernel.org/project/linux-wireless/patch/20230224135933.94104aeda1a0.Ie771c6a66d7d6c3cf67da5f3b0c66cea66fd514c@changeid/)
Is this patch automatically applied?
If not, what are the steps to apply a patch properly?

---

