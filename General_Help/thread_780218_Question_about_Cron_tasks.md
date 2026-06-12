---
title: "Question about Cron tasks"
date: 2008-05-03
forum: General Help
---

### Post by jobsonandrew on 2008-05-03
Hi All,
I just wrote a couple of scripts to change my desktop wallpaper at certain times.. I used the GUI:
```
sudo apt-get install gnome-schedule
```
then **System** -> **Preferences** -> **Scheduled Tasks**

But my friend raised an interesting question about Cron (and scheduled tasks in general)...

My first script is set to run at 8am Monday through Friday.. but what if the machine is not turned on at the time of the scheduled task.. e.g. if I turn the machine on at 8:05am will it know that it should have run that task 5 mins ago and run it at 8:05?

---

### Post by RealPSL on 2008-05-04
Regular cron is not aware of "missed times". If you want to run jobs after the original times have been missed the anacron program will solve that problem.

---

