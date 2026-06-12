---
title: "Is my router on it's way out"
date: 2016-06-16
forum: General Help
---

### Post by Superdude_123 on 2016-06-16
Is there a way to see a time stamp of when my wireless network connection was up or down, and what IP it got assigned to at that time? I'm trying to use my Linux system logs to see how frequently my router might be dropping out and see if there's any thing that I am doing elsewhere on the network that I can correlate.

---

### Post by &amp;KyT$0P# on 2016-06-16
Not sure about 11.10 but at least in 14.04 that information should be in /var/log/syslog.  Try something like this command?
```
grep -F -i NetworkManager /var/log/syslog | less
```
(if you don't like the wraparound, use less -S instead of just less)

---

### Post by Habitual on 2016-06-17
Like this?
```
grep renew  /var/log/syslog
Jun 17 07:56:43 my-kungfu dhclient: bound to 192.168.1.3 -- renewal in 40376 seconds.
Jun 17 07:56:43 my-kungfu NetworkManager[948]: <info> (eth1): DHCPv4 state changed renew -> renew
```

---

### Post by Superdude_123 on 2016-06-25
Thanks Habitual! I ended up replacing my router, but that's exactly what I meant.

---

### Post by mörgæs on 2016-06-25
In case other people find the thread I would recommend updating the router firmware before the router itself.

---

