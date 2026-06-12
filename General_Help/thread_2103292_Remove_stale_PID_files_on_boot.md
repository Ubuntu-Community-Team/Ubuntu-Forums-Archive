---
title: "Remove stale PID files on boot"
date: 2013-01-09
forum: General Help
---

### Post by dub4u on 2013-01-09
I have an Ubuntu Server 12.04.1 LTS running the weather archiving software wview. The wview daemon puts it's PID file in /var/lib/wview/ and does not detect a stale PID file and thus refuses to start. So I need to run a small script that will remove these PID files but only do so on boot and also do this before wview starts (it currently starts at /etc/rc2.d/S99wview). I have no problem writing the script but I don't know how to make sure it runs at the correct time.

---

### Post by dcstar on 2013-01-10
> **dub4u said:**
> I have an Ubuntu Server 12.04.1 LTS running the weather archiving software wview. The wview daemon puts it's PID file in /var/lib/wview/ and does not detect a stale PID file and thus refuses to start. So I need to run a small script that will remove these PID files but only do so on boot and also do this before wview starts (it currently starts at /etc/rc2.d/S99wview). I have no problem writing the script but I don't know how to make sure it runs at the correct time.

Call the script from /etc/rc.local with a sleep command in it to allow the system to fully boot before it is executed.

---

### Post by dub4u on 2013-07-08
For what it's worth, I ended up doing this through cron's @reboot function.

---

