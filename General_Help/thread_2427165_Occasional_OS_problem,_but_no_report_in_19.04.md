---
title: "Occasional OS problem, but no report in 19.04"
date: 2019-09-18
forum: General Help
---

### Post by Edward_Diener on 2019-09-18
In 19.04 occasionally, but usually soon after logging in, I get a pop-up dialog telling me that there has been some OS problem and do I want to report it, with two buttons of Cancel and Report Problem... . I do not even have to do anything to have this pop-up dialog occur. If I click the Report Problem... button the dialog goes away and nothing further happens with the problem. I can continue to use Ubuntu 19.04 and nothing seems tro occur that is wrong with the OS. When I look in the Logs I see:

"gnome-session-b
Unrecoverable failure in required component org.gnome.Shell.desktop
Priority 3"

Is anybody else getting this who might know why I am experiencing this problem ? It almost always occur early after a login, but does not affect my further use of 19.04. Rarely does it occur again while I am using Ubuntu but sometimes it subsequently pops-up again. It would be nice to figure this out so that it does not occur again. Running Ubuntu 18.04 on the same hardware I never saw this problem.

---

### Post by deadflowr on 2019-09-18
See if you have a report in /var/crash.

---

### Post by sdsurfer on 2019-09-19
And your system otherwise seems to run normally after that? Is it possibly similar to [this]("https://ubuntuforums.org/showthread.php?t=2425037"), even though I'm reporting in 18.04?

Sorry there are no answers in that link but have been scouring these forums and the web for a clue.

---

### Post by Edward_Diener on 2019-09-19
> **deadflowr said:**
> See if you have a report in /var/crash.

Thank you ! I do see some crashes there. One was for cups and another recent one is for wget. It also seems like I am now experiencing much fewer OS problems than before. Perhaps some update is fixing the crashes.

---

