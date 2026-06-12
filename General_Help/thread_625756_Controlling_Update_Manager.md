---
title: "Controlling Update Manager"
date: 2007-11-28
forum: General Help
---

### Post by gmc on 2007-11-28
Hi Folks,

Does anyone know how to control the time of day that Ubuntu checks to see if there are any updates? I have a couple that try competing with each other for bandwidth when there are updates (especially large one's like Open Office).

I'd like to set one machine to check at midnight and the other one at 4am so they don't both check at the same time. It also will allow me to cache the files from the first attempt so the second machine will get it's updates quicker.

Thanks
Gord

---

### Post by monktbd on 2007-11-29
not sure about gutsy but in dapper the session autostart starts "update-notifier" (in system-preferences-sessions). you could put that either in a gnome scheduler (if there is one) or into crontab for the time you want it to start.

---

### Post by gmc on 2007-11-30
I think I found what I was looking for. In /etc/crontab there's an entry for daily/weekly and monthly. I just changed the time for the daily event.

Thanks
Gord

---

