---
title: "memory/cpu monitoring with prtg (or another tool)"
date: 2016-02-09
forum: General Help
---

### Post by NotQuiteSU on 2016-02-09
I currently am using PRTG, but am open to any other tool. I want to be able to monitor and track memory/CPu usage of my Ubuntu 14 LTS server. I don't see anything by default within PRTG or the MIB for Ubuntu.

Is there a good way to do this?

---

### Post by ajgreeny on 2016-02-09
This might not be quite what you're looking for but the desktop system-monitor conky can show you that very easily (as well as a lot of other info, should you want it).  Does your server have a GUI?

Here's my conky window on the desktop of my machine.

It is showing the 4 cores of my CPU and the processes using them; below that is the partition usage of the system, and then the RAM and swap usage.  I also show network statistics, and cpu & disk temperatures.

If that looks interesting ask again for more info on how I get to that output and I'll answer as quick as I can.

---

### Post by NotQuiteSU on 2016-02-09
no gui on mine, thank you though. I'm also looking to monitor remotely, not just locally

---

