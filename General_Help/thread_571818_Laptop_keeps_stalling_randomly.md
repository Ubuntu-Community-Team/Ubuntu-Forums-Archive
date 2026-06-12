---
title: "Laptop keeps stalling randomly"
date: 2007-10-09
forum: General Help
---

### Post by kybishop on 2007-10-09
I have a Dell 1420n, the n means ubuntu was pre-loaded, which I clean installed with Gutsy Kubuntu 7.10

Everything was working perfectly until today; my laptop has started stalling for a second or two every minute or so.

If I'm pressing a keyboard key while the laptop stalls it'll print up to 15 or so of the character that was pressed after it comes unfrozen.

Music stutters constantly until the freeze is over.

Nothing triggers the stuttering (as far as I know).

Thanks for any help, Kyle.

---

### Post by likemindead on 2007-10-09
Post your most recent log file so that people can examine what's going on.

---

### Post by kybishop on 2007-10-09
Where's it stored?

---

### Post by p_quarles on 2007-10-09
You can get a list of your log files by typing:
```
ls /var/log
```
The ones I'd pay attention to are:
/var/log/syslog
/var/log/dmesg
/var/log/acpid
/var/log/kern.log

If you paste all of those here, no one's going to read them, though (we're talking a *lot *of info). First, look through them for any error messages that occur around the time of one of these freezes, and let us know what you find.

---

