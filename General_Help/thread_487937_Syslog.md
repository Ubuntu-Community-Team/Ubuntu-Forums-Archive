---
title: "Syslog"
date: 2007-06-29
forum: General Help
---

### Post by Soda Ant on 2007-06-29
I'm having a strange problem with Syslog. The system logs (/var/log/messages, /var/log/syslog) are getting rotated every morning properly, but then logging stops completely. The log rotator renames syslog to syslog.0 and creates a new syslog file, but nothing ever gets logged to it. The file size stays at 0 bytes.

If I restart sysklog, (/etc/init.d/sysklog stop; /etc/init.d/sysklod start), logging starts normally again.

This is a new install of 7.04 and I haven't changed the syslog or log rotate config files.

Is this a know problem? How do I fix it?

---

### Post by Soda Ant on 2007-07-06
Anyone?

---

### Post by Velli76 on 2007-08-23
I have exactly the same problem with two servers also! Does anyone have a fix for this?

---

### Post by Velli76 on 2007-09-13
I installed syslog-ng and it is working, no more syslog-freezings.
Latency is much better with Syslog-ng, default syslog-server in Ubuntu 7.04 doesn't seem to work that well. :(

---

