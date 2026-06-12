---
title: "System Problem Reporting at Boot/Desktop"
date: 2019-09-14
forum: General Help
---

### Post by Quarkrad on 2019-09-14
For sometime I have had a system problem reported when I boot to my Desktop (attached) - I have not found the problem and my /var/log folder has grown extremely large.  Any help on what the problem is would be appreciated (when I press the Report Problem button it just *reports* and the window disappears. I do not get the option to see what the problem is that is being reported).  The systemlog shows:

[https://paste.ubuntu.com/p/Bcgp8pS8Nb/](https://paste.ubuntu.com/p/Bcgp8pS8Nb/)

---

### Post by guiverc on 2019-09-14
Did you look in /var/crash/ for any crash reports.  When you report the crash; it's the contents of this that are uploaded; and you can view these files as they are text (any binary components are stored as a hexdump so text readable if you understand gibberish), but the name particularly is a huge clue as to where the problem was, date/time stamp of when, plus the start of the crash-file is pretty understandable.

---

### Post by Quarkrad on 2019-09-14
I had three files in /var/crash - the latest one included details on my caja file manager.  However, I deleted all three files and since then I have not had the Problem Notification - seems to have addressed the problem. Many thanks.

---

### Post by Rubi1200 on 2019-09-14
The program responsible for crash reports is called Apport.

More information here, including how to disable those pop-ups appearing after booting:
[https://itsfoss.com/how-to-fix-system-program-problem-detected-ubuntu/](https://itsfoss.com/how-to-fix-system-program-problem-detected-ubuntu/)

---

