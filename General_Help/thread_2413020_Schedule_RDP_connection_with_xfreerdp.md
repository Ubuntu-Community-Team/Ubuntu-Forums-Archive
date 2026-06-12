---
title: "Schedule RDP connection with xfreerdp"
date: 2019-02-20
forum: General Help
---

### Post by edoardo.ceccarini.ares2t on 2019-02-20
Hi guys,
I need to schedule a rdp connection every day but if i use crontab it doesn't work.
How can i schedule it?
I use xfreerdp from terminal to open the connection normally.
Thank you!

---

### Post by edoardo.ceccarini.ares2t on 2019-02-21
Ok I did it myself.
I wrote a script that will be run on startup that will launch a xfreerdp command.
And then I have set in the crontab a reboot every day at 00:00 am.
Thank you anyway!

---

