---
title: "tracker, tracker-extract, tracker-store: CPU hogs"
date: 2017-07-22
forum: General Help
---

### Post by themeadows94 on 2017-07-22
Via tracker-gui, I've set tracker to not operate on battery, or when the computer is being otherwise used. Tracker does not respect these settings. CPU usage of these utilities never drops below 20%. I'd prefer not to uninstall them because having indexed files is very occasionally useful, but is there any way to directly limit the amount of CPU they use? I've tried cpulimit, which hangs on the following command:

> $ cpulimit -e tracker-store -l 3Process 2422 detected


Any ideas how to stop tracker wiping out my battery life?

---

