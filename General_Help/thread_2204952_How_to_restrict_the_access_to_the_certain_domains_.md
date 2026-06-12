---
title: "How to restrict the access to the certain domains during work hours automatically"
date: 2014-02-11
forum: General Help
---

### Post by earlybird2 on 2014-02-11
I know about SelfControl app, but it has to be started everytime and the block hours to be set.
  I want for example to forbid loading certain sites during work hours,  but make it possible during the rest. I want to set it once and forget.  It has to do the switch automatically everyday.
  What would be the easier way to do this, considering that i'm a super newbie. It needs to work just for my PC not a network or something.

---

### Post by tfrue on 2014-02-11
My thought would be edit your router configurations, but you could probably set up iptables on your computer to block websites; but the only way I can make that work in my head is to set up cron jobs to create the iptable filters and delete them at certain times everyday.

---

### Post by dragonfly41 on 2014-02-11
As I added to a nearby thread .. there is nanny in Ubuntu Software Centre for "parental controls".

[http://linuxers.org/article/gnome-nanny-parental-control-system-linux](http://linuxers.org/article/gnome-nanny-parental-control-system-linux)

I don't know whether OpenDNS provides date/time filters.

---

### Post by Lars Noodén on 2014-02-11
iptables can block based on time of day and day of week.  See [iptables-extensions](http://manpages.ubuntu.com/manpages/saucy/en/man8/iptables-extensions.8.html) section on --timestart, --timestop, and --weekdays.  Use the 'reject' target to prevent wasting time waiting for the inevitable timeout.

---

