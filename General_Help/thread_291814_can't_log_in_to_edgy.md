---
title: "can't log in to edgy"
date: 2006-11-03
forum: General Help
---

### Post by aanderse on 2006-11-03
a friend of mine's computer (ubuntu6.10) crashed today (he's not sure why) and when he tried to log back in he got the following error:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "lyndsay"
/etc/gdm/Xsession: Beginning session setup...
mkdtemp: private socket dir: No space left on device


any ideas?

---

### Post by H.E. Pennypacker on 2006-11-03
Your friend is filling up her/his harddrive without paying attention to the harddrive's limits.  Ubuntu should have been telling her/him that she/he was going overboard, but the message must have been ignored.

Using a Google (Google.com/linux for Linux-only results) search quering the key terms ("No space left on device"), and adding "Ubuntu" to narrow search results, I found the following helpful article:

[URL="http://arun-prabha.com/wdpress/?p=301"]
Fixing No space left on device error in Ubuntu Linux[/URL]

---

