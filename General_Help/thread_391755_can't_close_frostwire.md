---
title: "can't close frostwire"
date: 2007-03-23
forum: General Help
---

### Post by Pyro_Killer on 2007-03-23
I have installed froswire on my ubntu, and it works well, but I can't close it. Plz help me, and how can  view all my processes?

---

### Post by ajgreeny on 2007-03-23
To view all your processes graphically use gnome-system-monitor.  There is also a terminal command that will list them all, but for the moment I can't remember it.

OK I've found it. "ps -ef" in terminal

"top" in a terminal will tell you a lot about what is using your machine's resources, but is not a complete list, I don't think.

---

### Post by xurizaemon on 2007-04-05
Put down that hammer. Frostwire thinks you want it to finish its downloads, *THEN* quit.

**Tools -> Options -> System Tray -> Shutdown Immediately** should fix this.

IMO, this is a stupid default to have set on install. But the Frostwire package is not in default Ubuntu, so it's something to bother the Frostwire team about.

---

### Post by loafula on 2007-08-05
> **xurizaemon said:**
> Put down that hammer. Frostwire thinks you want it to finish its downloads, *THEN* quit.

**Tools -> Options -> System Tray -> Shutdown Immediately** should fix this.

IMO, this is a stupid default to have set on install. But the Frostwire package is not in default Ubuntu, so it's something to bother the Frostwire team about.

wow. i've been having this problem with frostwire for nearly two months. i always figured it was a glitch and never bothered to look into it. worked like a charm!

---

