---
title: "Red screen of death using new nvidia drivers and a cryptic error message in syslog"
date: 2012-12-14
forum: General Help
---

### Post by J V on 2012-12-14
Using 310.14 I got a "Red screen of death" where the whole screen went full on [COLOR=Red]#FF0000 red.[/COLOR]

At first I thought the cable was loose but after a reboot syslog had a cryptic error message:

```
NVRM: Xid (0000:01:00): 16, 
Head 00000000 Count 00006e2e
```Should I worry?

---

### Post by dino99 on 2012-12-14
you should use the latest 313 from xorg-edgers ppa

---

### Post by J V on 2012-12-14
Every time I've installed xorg-edgers it's bricked my GUI.

Followed by several hours of manually removing broken dependancies etc, etc...

But I'll install them manually then.

---

