---
title: "crontab edit fails with E212"
date: 2006-10-10
forum: General Help
---

### Post by Ben Branch on 2006-10-10
Hi,

I'm trying to use "crontab -e" to edit a crontab. Any crontab.
My own, or, via sudo, root's crontab. Whatever I do, the editor
complains about "crontab.hRI6Gz/crontab: E212: Cannot open file
for writing". (The hRI6Gz is apparently a random string, it's
different every time). The gvim banner makes it appear that
crontab.hRI6Gz (or whatever) should be a subdirectory of /tmp,
but it's not there. Creating it manually doesn't help.

Thanks in advance for all suggestions and pointers ...

Ben

P.S. Why isn't there a decent GUI to do this???
Edit: I found gcrontab and it's not perfect but if it works, it'll do.

---

### Post by subzero79 on 2006-10-10
I strongly recommend you to use the search function of the Synaptic Package Manager.

a GUI frontend for cron is gnome-schedule for GNOME an KCron for KDE. Personally i recommend KCron It works the same in GNOME.

---

