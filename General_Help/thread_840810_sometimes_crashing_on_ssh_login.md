---
title: "sometimes crashing on ssh login"
date: 2008-06-25
forum: General Help
---

### Post by Aero Leviathan on 2008-06-25
Hi there,

I'm having a problem in which my machine will crash maybe 10-20% of the time that I login remotely via SSH. It's been running Ubuntu for a year or so now and this has only started happening recently, perhaps within the past month or so... can't say for sure whether it coincided with the Hardy upgrade.

When I login, it will crash right after the 'Last login: <date> <time> from <host>' message, but before it displays the bash prompt. At this point I cannot connect to any service on any port and GNOME is unresponsive. I've never had this happen while using a local terminal or any GUI app, but that's not to say it won't happen because I more commonly use the machine over SSH.

At first I assumed it was a bad hard drive, which I had suspected for unrelated reasons. Several days ago I replaced the hard drive with a brand new one and did a fresh install of Ubuntu (bringing only my home directory from the old machine), but then the problem happened again today.

I ran memtest86+ from the boot menu, no errors found so far after several passes.

Specs:
hp pavilion a210n
1x 2.50 GHz Intel Celeron
512 MB RAM
Ubuntu 8.04 (hardy)

I understand this is probably not specific enough for any kind of diagnosis, but I was wondering if anyone had tips for where to look? For example, a crash log of some kind?

TIA...

---

### Post by Aero Leviathan on 2008-06-26
As it happened again today, I was poking around in /var/log, and found some cron activity going on in syslog even after the machine 'crashed'. It even had a 'reboot' entry for when I came home and power cycled it. So it appears it is still operating at some low level even after it becomes unresponsive. Anywhere else I could be looking?

---

