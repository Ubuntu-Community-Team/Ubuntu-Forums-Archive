---
title: "Workspace Switcher bug"
date: 2015-09-30
forum: General Help
---

### Post by ra7411 on 2015-09-30
I ran into the Workspace Switcher bug a few times today. Sometimes, when moving an app from one space to another, things seized up, and I had to power off and power up. The last time I got out of it by hitting super+s.

Is there any way of curing this thing, or unfreezing it, besides super+s ?

Thanks

---

### Post by cariboo on 2015-09-30
It would help if you told us which version you are using.

---

### Post by ra7411 on 2015-09-30
>[COLOR=#000000]It would help if you told us which version you are using.<

Ub 14.04

[/COLOR]

---

### Post by tgalati4 on 2015-10-01
Look for errors:

```
more ~/xsession-errors
more /var/log/Xorg.0.log
```

It's possible that you have a video RAM problem; when you switch workspaces, different parts of video RAM are used.  This is not easy to diagnose.

---

