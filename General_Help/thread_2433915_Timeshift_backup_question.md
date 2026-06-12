---
title: "Timeshift backup question"
date: 2019-12-27
forum: General Help
---

### Post by ra7411 on 2019-12-27
With most backup programs I've used you pick a partition you want to back up and a partition to send the backup to.

Timeshift seems to assume the o/s you're in and that Timeshift is running from is what you want to backup, and you select whether to include home, .hidden, and then what partition to send it to, right, or am I overlooking something?  

Thnx

---

### Post by rbmorse on 2019-12-27
Timeshift is designed to backup only the working system, not the user data files. It's not really backup as most people understand it and should not be used as such.  

OTOH, it's damned handy for making a quick snapshot of the system before installing new hardware or system drivers, or making other significant changes to the system.  If things go bad you can put things back to just how they were at the time the snapshot was made with just a few clicks.  The dwell time between snapshot creation and point things went bad will determine the effectiveness of the recovery.

---

### Post by GhX6GZMB on 2019-12-27
+++1
rbmorse said it
The source of a Timeshift backup is your current system. It wll backup all configurations and installed programs. What it will normally not backup is your kernel (/root) and your documents (/home).
The only thing you need to select is the backup target (ext4 formatted).

If you think Timeshift will backup Windows in a dual-boot system: forget it!

---

