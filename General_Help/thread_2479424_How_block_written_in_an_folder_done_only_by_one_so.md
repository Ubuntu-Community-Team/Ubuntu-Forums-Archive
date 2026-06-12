---
title: "How block written in an folder done only by one software ?"
date: 2022-09-24
forum: General Help
---

### Post by aug7744 on 2022-09-24
Hello.
Have an software doing an high number of written in /tmp.
The files are only for performance logging. The software not allow disable logging.
The files are named "perf-xxxxx.map" being xxxx = random numbers.

How block written in /tmp for that software ? Is possible any other way to avoid creating "perf-xxxxx.map" files ?

Thanks for reply.

---

### Post by The Cog on 2022-09-24
You could run the sotware in a wrapper called bubblewrap (the executable is  /usr/bin/bwrap). You should be able to give it normal access to / (which is has when not wrapped), but readonly access to /tmp. Or you could give it a virtual (in-memory) /tmp that it can write to but isn't real.
I couldn't quickly find a good tutorial, just these below. But I have used it and it works. 
[https://www.systutorials.com/docs/linux/man/1-bwrap/](https://www.systutorials.com/docs/linux/man/1-bwrap/)
[https://lwn.net/Articles/686113/](https://lwn.net/Articles/686113/)
[https://wiki.archlinux.org/title/Bubblewrap](https://wiki.archlinux.org/title/Bubblewrap)

---

### Post by The Cog on 2022-09-24
More info, now I have had time to try things out. Below are two commands that launch bash. The first allows the child process to see the contents of /tmp but read-only. The second command replaces  /tmp with a temporary virtual folder that it can write to but nobody else can see.
```
bwrap --dev-bind / / --bind-ro /tmp /tmp /bin/bash
bwrap --dev-bind / / --tmpfs /tmp /bin/bash
```
You can launch other processes instead of bash this way of course - you didn't say the name of your software.

---

