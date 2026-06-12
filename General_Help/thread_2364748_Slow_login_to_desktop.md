---
title: "Slow login to desktop"
date: 2017-06-27
forum: General Help
---

### Post by CatKiller on 2017-06-27
I'd been having problems with a delay logging into the desktop. Not stupidly long, but annoyingly so; about 20-30 seconds or so.

I fiddled around with the startup programs, and nothing seemed to make a difference.

By chance I happened to spot that there were a whole bunch of instances of apport-gtk running at that time. I deleted all the crash reports from /var/crash and everything is fine now.

Hopefully this will help anyone else with the same problem.

---

