---
title: "Run a Program in the background at boot"
date: 2018-10-08
forum: General Help
---

### Post by misaalanshori on 2018-10-08
I'm trying to start [Musikcube]("https://musikcube.com/") at boot in the background because it has an internal music streaming server. I want to be able to have it automatically run in the background after the computer turns on.

other things that might be important:
the computer is running ubuntu 18.04 without a monitor, so i'm connecting to it with ssh or xrdp
power outages happens a lot in here so the computer would turn off without a proper shutdown, but the computer automatically turns on when it gets power

---

### Post by TheFu on 2018-10-08
Step 1) get a UPS.  Unplugging any Unix-based computer is dangerous.  Eventually, you'll end up with a system that refuses to boot.

Step 2) Create a systemd start/stop config file for any daemons you want controlled.  There are examples on the system already and there are some examples in these forums already.  Be certain to get the daemon dependencies correct.  It makes no sense for streaming server to be up if there isn't any networking yet.

Use **sudoedit** to create and edit any  system files.

Step 3) tell systemd to enable the service at boot.

If I knew the exact commands, I'd put them in here.  I'd have to search for the exact answer.

---

