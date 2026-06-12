---
title: "notification-daemon crashes on boot"
date: 2013-06-02
forum: General Help
---

### Post by fizikz on 2013-06-02
I've had a problem for a while now where notification-daemon crashes when I boot, and then again many times when icons change/appear/disappear in the notification area. It has never impacted functionality or performance to my knowledge, but it's just annoying to keep seeing "Sorry, Ubuntu 12.04 has experienced an internal error"

The actual error in the report is:

```
notification-daemon crashed with signal 5 in g_return_if_fail_warning()
```

Is there a solution to this? I've googled the error and came up with many posts but none seemed conclusive.

---

### Post by sandyd on 2013-06-02
Try enabling the precise-proposed sofware repo (Software Center -> System Sources)
[https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/926758](https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/926758) (fixed in precise-proposed)

---

### Post by fizikz on 2013-06-03
Well, what do you know... that seems to have worked! I just enabled precise-proposed updates, updated the system, and rebooted to see if I get anymore crashes. So far, none. I was a bit wary of enabling proposed updates since I want this system to be as stable as possible. It looks like they might just have helped with stability. Thanks!

---

### Post by fizikz on 2013-06-03
Well, it seems it's not really solved. Notification-daemon still crashes sometimes, especially when I close popup notifications that appear in the upper right-hand corner of the screen. The error message about notification-daemon crashing is the same.

Also, I'm not getting popup notifications from pidgin anymore, although the notification sound still plays.

---

