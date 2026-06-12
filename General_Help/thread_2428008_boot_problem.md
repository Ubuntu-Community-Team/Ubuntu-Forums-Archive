---
title: "boot problem"
date: 2019-09-28
forum: General Help
---

### Post by jgw on 2019-09-28
I am having a problem booting up.  Sometimes it works, sometimes it doesn't.  I have noticed, however, when its booting and showing stuff, the there is an error that says something like: "system journal corrupt" (not sure because if flies right on by).

I have also noticed that, when there is going to be a problem the Unix dot,dot, dot, dot pages start to blink on and off (each blink different).  This goes on for a long time, there is no disk activity.  
I have gone to the grub menu and  updated grub, I have also gone through that menu, one choice after another, and chosen each line (check file menu, etc).  to no avail.  
I have also edited my grub file to have the option to choose to get to recovery mode/menu

Thoughts?

---

### Post by Bashing-om on 2019-09-28
jgw; Hello Again:)

thoughts:
1) have a look at the boot log:
```

journalctl -b -0

```
2) run a file system check/repair from the liveDVD/USB
3) See what you can find in the system log file:
```

less -S+G /var/log/syslog

```

[INDENT]until you know
[INDENT][INDENT]there is no point in pulling a trigger
[/INDENT][/INDENT][/INDENT]

---

