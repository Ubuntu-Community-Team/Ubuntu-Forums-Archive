---
title: "Apport-autoreport...Howto resolve this?"
date: 2024-11-17
forum: General Help
---

### Post by wyattwhiteeagle on 2024-11-17
Syslog has the following message.
How do I resolve it?
```
apport-autoreport.timer - Process error reports when automatic reporting is enabled (timer based) was skipped because of an unmet condition check (ConditionPathExists=/var/lib/apport/autoreport).
```

---

### Post by 1fallen on 2024-11-17
Please also include this:
```
[FONT=monospace][COLOR=#000000]sudo systemctl is-enabled whoopsie.path[/COLOR]

```


[/FONT]

---

### Post by wyattwhiteeagle on 2024-11-17
> **1fallen said:**
> Please also include this:
```
[FONT=monospace][COLOR=#000000]sudo systemctl is-enabled whoopsie.path[/COLOR]
[/FONT]
```
Terminal say's
```
enabled
```

---

