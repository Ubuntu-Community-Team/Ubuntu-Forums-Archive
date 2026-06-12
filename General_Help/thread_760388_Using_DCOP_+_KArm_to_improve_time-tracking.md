---
title: "Using DCOP + KArm to improve time-tracking"
date: 2008-04-20
forum: General Help
---

### Post by KIAaze on 2008-04-20
I discovered KArm recently, and through it's user manual, the great [DCOP system]("http://developer.kde.org/documentation/other/dcop.html").
This allowed me to write a daemon-like bash script which improves KArm.

Here's what it does:
-It checks every second if a KDevelop project is open.
-If yes, and a task in karm with the same name as the project exists, it starts it.
-If such a task doesn't exist it creates it.
-If the project or KDevelop is closed, it stops the corresponding timer.
-If the KDevelop window hasn't been focused for x seconds, it displays a warning message and stops the timer.

The number of seconds can be changed easily in the script at line 10.
You can also change the timestep of the while loop at line 8.

Suggestions for improvements are very welcome.

To use it:
-Set KArm and the script to run at startup through system->preferences->sessions.

I hope others will find this useful too.
The best would of course be to integrate such a feature into KArm. But for the time being this works well.

Here's the script:

---

### Post by morbid_bean on 2008-12-11
thanks!

---

### Post by KIAaze on 2008-12-11
Glad to know you find it useful. :)

---

