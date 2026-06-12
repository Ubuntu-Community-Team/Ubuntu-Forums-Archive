---
title: "Chromium startup"
date: 2016-02-03
forum: General Help
---

### Post by Edward 000 on 2016-02-03
Firefox and Chrome open instantly but Chromium needs 6 secs to open even with Preload installed , how can I make it open instantly?

---

### Post by TheFu on 2016-02-05
"Instantly"?  Can't be done for any program. There is always load time. Always.  Even if you pre-load it and minimize the window, the act of bringing that window to the front takes a tiny amount of time.

FYI, on my Core i5 system, running a lite-desktop inside a VM and accessing it using x2go (remote desktop), Chromium takes about 15 seconds to launch. Don't really use it much. I don't know how long firefox takes, since it gets started once after a reboot and I leave it running until the next reboot.  Whenever I reconnect via x2go, firefox is always there, running, already.

If you want to see what is taking chromium so long, you can run a profiling tool like **strace**. [http://www.cyberciti.biz/faq/howto-use-linux-truss-strace-command/](http://www.cyberciti.biz/faq/howto-use-linux-truss-strace-command/) Not too hard if you are a C programmer. I just used it here - seems like chromium is writing to logs - A BUNCH and constantly asking gettimeofday() for what time it is.  At the startup, it seems to be looking for which X11 compatibility files are available, checking for how much RAM the system has, then looking for and loading any plugins.  That's the first 1% of the trace file. Then it starts looking at themes, local storage, printing support, bluetooth stuff, multimedia capabilities, TLS support, and it goes on and on.

The manpage talks about initial setting files, but doesn't talk about what settings can/should be placed into those files.  Basically, chromium is an entire OS and needs to load up stuff that most OSes need. I cannot say why/if chrome is faster. I won't run a browser created by the largest advertising company on the planet.

---

