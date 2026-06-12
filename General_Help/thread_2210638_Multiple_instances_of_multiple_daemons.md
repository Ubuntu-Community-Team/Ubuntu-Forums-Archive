---
title: "Multiple instances of multiple daemons"
date: 2014-03-11
forum: General Help
---

### Post by Tristan_Williams on 2014-03-11
I am running Ubuntu Minimal 13.10 with Xfce4

This may be normal, but it just seems odd to me.

When I run "htop", I see multiple instances of the exact same process. Some of these include:
 - NetworkManager (4 instances)
 - rsyslogd -c5 (4 instances)
 - /usr/bin/colord/colord (3 instances)
 - lightdm (4 instances)
 - /usr/sbin/console-kit-daemon --no-daemon (30-40 instances, I lost count)
 
That is just the ones towards the top of the "RAM usage"

Is this normal? 
If it's not normal, how do I fix it?

---

### Post by ian-weisser on 2014-03-11
It does not seem normal to me...but I don't use htop.
Fixing it means you must figure out what's causing it.
NetworkManager and rsyslogd spawn during boot from upstart jobs in /etc/init
Lightdm spawns during boot, and respawns upon x logout, also from /etc/init.
ConsoleKit operates every time a login, logout, or some hardware changes occur. Starting with --no-daemon seems unusual in itself.

Have you, by chance, been mucking with /etc/init or /etc/init.d?
How long after a reboot or login or logout do the duplicates start to propagate?

---

### Post by Tristan_Williams on 2014-03-11
No I've never messed with /etc/init or /etc/init.d

They seem to be duplicated immediately after reboot or login.

Still completely clueless

---

### Post by bab1 on 2014-03-12
> **Tristan_Williams said:**
> No I've never messed with /etc/init or /etc/init.d

They seem to be duplicated immediately after reboot or login.

Still completely clueless

It's all normal.  See [here]("https://bbs.archlinux.org/viewtopic.php?id=80101").  Maybe you should work on your Google Fu.  :-)

---

### Post by Tristan_Williams on 2014-03-12
The main problem is with teamviewerd.

---

