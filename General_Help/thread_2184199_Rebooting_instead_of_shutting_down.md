---
title: "Rebooting instead of shutting down"
date: 2013-10-28
forum: General Help
---

### Post by Buster95 on 2013-10-28
My old IBM Thinkcentre M-52 desktop, running 13.04 started rebooting on shutdown a month ago. It MAY have been after a routine update, but I'm not sure.

I couldn't spot the cause on the log files, so I tried an upgrade to 13.10 - but the problem persisted. The unwanted restarts occur whether I use the Shutdown option (menu bar "gear" icon) or Sudo Shutdown -P or Sudo Shutdown -H on a terminal.

I now shut down by holding the start button down during the inevitable restart. That works!

Any guidance on a fix would be appreciated.

---

### Post by petesuz on 2013-11-26
Mine too - I'm just testing 12.04 LTS on my soon to be EOL XP machines and it's happening to me too - despite turning off anything to do with it in BIOS. 
Weird. I'll let you know if I figure anything out.

---

### Post by bashiergui on 2013-11-26
It's a known bug. There is a work around here
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1002429](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1002429)

---

