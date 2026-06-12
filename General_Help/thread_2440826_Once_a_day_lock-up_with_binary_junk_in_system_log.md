---
title: "Once a day lock-up with binary junk in system log"
date: 2020-04-15
forum: General Help
---

### Post by MgFrobozz on 2020-04-15
I'm having problems with my ubuntu system (18.04.4 LTS x86_64) locking up up about once a day. When this happens, the mouse and keyboard are unresponsive. Today, it did that while I was in the middle of editing a text file. As in yesterday's lock-up, this appears as binary garbage in /var/log/syslog. I don't *think* anacron was causitive, since that's run pretty much every hour. 

In the log, the crash occurred around 14:03, and the cold-boot was around 14:06.

Does anyone have suggestions on how to trouble-shoot this?

```
[FONT=courier new]Apr 15 14:03:27 localhost anacron[23343]: Anacron 2.3 started on 2020-04-15[/FONT]
[FONT=courier new]Apr 15 14:03:27 localhost anacron[23343]: Normal exit (0 jobs run)[/FONT]
[FONT=courier new]^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@Apr 15 14:06:08 localhost systemd-modules-load[422]: Inserted module 'lp'[/FONT]
[FONT=courier new]Apr 15 14:06:08 localhost systemd-modules-load[422]: Inserted module 'ppdev'[/FONT]
[FONT=courier new]Apr 15 14:06:08 localhost systemd-modules-load[422]: Inserted module 'parport_pc'[/FONT]
[FONT=courier new]Apr 15 14:06:08 localhost systemd[1]: Starting Flush Journal to Persistent Storage...[/FONT]

```

---

### Post by lvm on 2020-04-16
Junk indicates that the lock-up was complete and so abrupt that system couldn't close/sync syslog properly, and these of course are the worst. Could be anything. Could be hardware - check temperatures, run memory test, check SMART, etc. Could be drivers. Just an off-hand chance: what video card are you using?

---

