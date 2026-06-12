---
title: "What log file to check"
date: 2020-06-30
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2020-06-30
When i woke the system from sleep mode, the system was unresponsive
* the keyboard numlock led as stuck as well
* i was able to reboot using [REISUB]("https://en.wikipedia.org/wiki/Magic_SysRq_key")
what log file should contain a error message for me to read as to why this happended

---

### Post by TheFu on 2020-07-01
Check all of them in /var/log/

I'd use **egrep -i 'erro|warn' /var/log/*g**

---

### Post by Holger_Gehrke on 2020-07-01
I'd also check the journal. 'journalctl -b ' followed by a negative number (-1 = logs from the previous boot, -2 the one before that, and so on).

Holger

---

