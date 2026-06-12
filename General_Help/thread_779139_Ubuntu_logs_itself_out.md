---
title: "Ubuntu logs itself out"
date: 2008-05-02
forum: General Help
---

### Post by notesetter on 2008-05-02
When the computer is idle for 8 or 10 minutes, it logs itself out and then displays the login screen.

I'm running Ubuntu Studio 8.04 on a Compaq Presario notebook:
2.0 Ghz
256 Mb RAM

Perhaps it's worth mentioning that I've never been able to get this to suspend or hibernate in Ubuntu.

This Windows-like behavior is distressing to me:confused:

Any thoughts?

Thanks

---

### Post by NilsE on 2008-05-02
Go into screensaver preferences and either turn of the lock option or increase the time.  You can also go into the configuration editor and alter the behavior under power management or screensaver there.

---

### Post by notesetter on 2008-05-02
Al of my settings under screensavers and power settings are set to "Never" The option to "lock screensaver" was unchecked. Also, when this happens, it programs close and data is sometimes lost. When I log back in, it's as if I just booted up.

I've seen it happen, where the screensaver is on, and then everything goes dark and text starts appearing on the screen. It acts as if it's shutting down or logging out. Then the login screen appears. I'm puzzled.

Thanks,

Dave

---

### Post by chrisccoulson on 2008-05-02
Sounds like Xorg crashing. What video driver do you use? Is there a backtrace at the end of /var/log/Xorg.0.log.old after the crash? Are you using desktop effects?

---

