---
title: "Multiple tasks blocked"
date: 2014-01-25
forum: General Help
---

### Post by remo3 on 2014-01-25
My server has been freezing frequently lately. It becomes completely unresponsive and I see the following on the screen:

```
[63842.596175] INFO: task pickup:16685 blocked for more than 120 seconds.
[63842.598703] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.

[63962.602425] INFO: task pickup:16685 blocked for more than 120 seconds.
[63962.604955] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.

[64082.614166] INFO: task showq:17539 blocked for more than 120 seconds.
[64082.616571] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
```

It just keeps going like this. Does anyone have any ideas?

---

