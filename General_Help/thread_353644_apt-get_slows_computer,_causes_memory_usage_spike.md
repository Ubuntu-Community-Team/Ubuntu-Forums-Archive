---
title: "apt-get slows computer, causes memory usage spike"
date: 2007-02-04
forum: General Help
---

### Post by becman on 2007-02-04
After a year of solving my own problems I've run into one where I have no idea.  The "setting up xxxx" portion of apt-get install xxxx causes a huge memory spike.  Normally my user memory idles around 20-30% usage.  As soon as the "settin up xxxx" portion of apt-get starts, the user memory spikes up to 92-98%.  X slows down to a halt, inputs take about 30 seconds each.  If I open a ctrl-alt-f1 terminal it is still extremely slow there.  This problem just started occuring the other day.  I don't recall installing anything or upgrading anything that would cause this problem.  After this the memory slowly goes back down to the normal usage level, but it takes about 15 minutes.  I'm using edgy.

Any ideas?

---

### Post by clouserw on 2007-02-05
Are you running out of space on your partition?  (Run `df -h`)

Is apt taking up the memory or something else? (Run `top` and type a capital M)

---

### Post by becman on 2007-02-05
20gigs free on root

top shows adept_notifier is the culprit, %mem goes to 90-95% usage 

still killing me

---

### Post by becman on 2007-02-06
removed adept-notifier
then apt-cache was the memory hog
i removed /etc/apt/apt.conf which had a cache size increase line

all seems to be working fine now

---

