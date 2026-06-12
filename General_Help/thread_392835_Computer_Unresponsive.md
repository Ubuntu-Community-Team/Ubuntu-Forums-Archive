---
title: "Computer Unresponsive"
date: 2007-03-25
forum: General Help
---

### Post by Kickboy on 2007-03-25
Recently my Ubuntu machine has been crashing during the night, and I haven't been able to determine why. It's happened 3 times in a row, each time after the computer has been on for about 3 days, and each time it happened during the night. I wake up and find my computer to be on (Fans running, power light on), but completely unresponsive. The monitor won't turn on, so I can't see any errors that may have popped up. Also I can't access it remotely; all connections (SSH,FTP,HTTP) go unanswered, but the machine is still running. My only option has been to do a force reboot.

Anybody have an idea what could be causing this, or at least know a way for me the determine the problem?

Thanks for any help you can provide.


Machine Specs:
Ubuntu 6.10
1.5 GHZ Athlon XP
512MB RAM
32MB GeForce2 MX PCI

---

### Post by user1397 on 2007-03-25
maybe a faulty hard drive?  very strange indeed...

sounds like an overheating problem too, if after 3 days of constant running, it does that.  try turning your computer off every night, and see if it ever happens again.

---

### Post by Kickboy on 2007-03-25
> **ubuntuman001 said:**
> maybe a faulty hard drive?  very strange indeed...

sounds like an overheating problem too, if after 3 days of constant running, it does that.  try turning your computer off every night, and see if it ever happens again.

Overheating is a possibility, but turning my computer off isn't an option. I use this as a development server, so it needs to be on all the time. Hence why this is such an issue for me.

I'll see if maybe this machine has some heat sensors I can access.

---

### Post by Kickboy on 2007-03-25
D'oh. I think I might have found the culprate.

I opened up my system monitor, and found a whole mess of sleeping "cron" processes. This is a direct result of a stats gathering system I am testing. Curious why the procesess aren't stopped after the cronjob has run. I have it setup to execute a specific PHP script every 30 seconds, so every 30 seconds a new cron process is added, and never stopped. I'm guessing after a while Ubuntu becomes a little overwhelmed and stops functioning.

Anyone have a solution to this?

Here's my crontab:

```

* * * * * php -f /www/cron/gather.php
* * * * * sleep 30; php -f /www/cron/gather.php

```

---

### Post by Kickboy on 2007-03-25
*bump*

Anybody? I really need a solution.

---

