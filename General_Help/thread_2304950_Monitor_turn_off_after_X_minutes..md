---
title: "Monitor turn off after X minutes."
date: 2015-12-01
forum: General Help
---

### Post by MrLukashem on 2015-12-01
Hello,

Very often (sometimes after 10min, sometimes after 4h) monitor turns off. I think is no signal on cable from GPU to Display. In my opinion computer works correctly, it means that I hear playing music etc. But screen is black.
After it occurs I have to reset my computer, beacouse I cant turn on my Display.

My GPU: Radeon R9 390.
OS: Ubuntu 15.10

Any suggestions?

---

### Post by deadflowr on 2015-12-01
10 minutes is the default screensaver timeout.
To change open System Settings and go to Brightness and Lock.
You can switch off the timer by setting it to never.

---

### Post by raketax on 2015-12-01
Tried replacing the monitor for test or simply clean the PC? Could be overheating. Also you could check the system logs in /var/log/dmesg, that could give you some idea on what goes wrong.

---

### Post by MrLukashem on 2015-12-01
Hello,
Thanks for answers. I will check settings, but I think I checked it last time. I will attach logs from /vat/log/dmesg soon. I recently reinstalled this OS, so it is fresh system (I decided to reinstall OS beacause same problem occured). I have windows 10 also on ssd (ubuntu on hdd) and all works fine. I will try with other monitor.

---

