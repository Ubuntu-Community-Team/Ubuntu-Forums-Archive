---
title: "System logging"
date: 2007-05-21
forum: General Help
---

### Post by gtorino on 2007-05-21
In my 6.06LTS server, /var/log/messages is filled with just lines of 
-- MARK --

Anyone know what this means, and how to set it to record useful information?

---

### Post by Jussi Kukkonen on 2007-05-21
It's just a timestamp. It's set with an option when syslogd is started, so I guess you could change that. I'm not sure that would be smart though: using dmesg or some grepping will make those MARKs invisible to you and the timestamps may come handy one day...

---

