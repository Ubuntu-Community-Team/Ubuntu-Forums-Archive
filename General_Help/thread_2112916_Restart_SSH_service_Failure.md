---
title: "Restart SSH service: Failure"
date: 2013-02-06
forum: General Help
---

### Post by alfirdaous on 2013-02-06
Hello everybody,

I would like to restart SSH service, but it failed:

```
service ssh restart stop: Rejected send message, 1 matched rules; type="method_call", sender=":1.96" (uid=1000 pid=8341 comm="stop ssh ") interface="com.ubuntu.Upstart0_6.Job" member="Stop" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init") start: Rejected send message, 1 matched rules; type="method_call", sender=":1.97" (uid=1000 pid=8338 comm="start ssh ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")
```

Thanks for your help

---

### Post by alfirdaous on 2013-02-06
permission issue

---

