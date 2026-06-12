---
title: "Crashing at Desktop"
date: 2015-12-12
forum: General Help
---

### Post by Quarkrad on 2015-12-12
One of the laptops (friend) I look after has suddenly started crashing when it gets to the Desktop (his on 12.04).  This is a fairly old machine but has been running without any trouble since I installed 12.04 so I know the base h/w is OK.  He unfortunately crashed the machine during a recent update so I (remotely) did a clean-up and upgrade.  He was on kernel 3.2.0.94 and is on 3.2.0.95 but it still crashes.   The only way to get in is to hold the Shift key during boot (to load grub) - go into recovery mode and RESUME a normal boot.   Then the laptop works OK.   I have looked on the web into this issue but most responses talk about the graphics driver being the culprit.  (He has an intel chip, mobile 4 graphics).   I have updated his graphics, reverted him back to 3.2.0.94 and 3.2.0.93 but the things still crashes at the Desktop.  At this point I will do a rebuild rather than spend hours on it but we are 90 miles away from each other.  One last thought - would it be worth clearing some of the system logs and then do a normal boot a see what is causing the crash? If so, what logs should I delete?

---

### Post by mikewhatever on 2015-12-12
As "crashing" is a vague term, to put it mildly, can you describe what actually happens in details.
Checking the logs is a good idea, but deleting logs before that doesn't make any sense.

---

### Post by Quarkrad on 2015-12-12
If one tries a normal boot the laptop goes through bios and then Ubuntu loads in the normal manner - when the desktop wallpaper is displayed on the screen the laptop powers down, almost instantly.

---

### Post by mikewhatever on 2015-12-12
OK, that's clear now. Do you still want to delete logs?

---

### Post by Quarkrad on 2015-12-13
Yes - I'm familiar with various logs in /var/logs such as syslog - but there are many more in that folder, and there may be more logs elsewhere.  I'm hoping if I clear some of these logs, then do a re boot, a log somewhere might help me see what is possibly causing the crash.  Things is, what log is best to clear?

---

### Post by mikewhatever on 2016-01-02
I would not clear anything. Logs are rotated in such a way that you can always see the latest, without resorting to unnecessary purges. If anything, deleting logs may well remove valuable evidence.

---

