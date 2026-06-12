---
title: "Ubuntu 12.04 crashing alot lately?"
date: 2013-04-18
forum: General Help
---

### Post by boy18nj on 2013-04-18
i copy pasted the log from log file viewier syslog [http://pastebin.com/6V6WZTKd](http://pastebin.com/6V6WZTKd)

I don't know what is causing the crash, may be chrome is causing it because whenever it crashed chrome is always running. i never had any problem with chromium. it's now very disturbing, when ubuntu suddenly crashes and no key works. even TTY won't work.

Also i am adding the snapshot after it hanged and stuck on screen. Please let know how to fix this.

[ATTACH=CONFIG]241498[/ATTACH]

---

### Post by sanderj on 2013-04-18
Q: why run chrome and not chromium?

I googled "comm: chrome-sandbox Tainted:" for you, and "google-chrome -no-sandbox" is suggested as work-around (see [http://lists.debian.org/debian-kernel/2010/09/msg00116.html](http://lists.debian.org/debian-kernel/2010/09/msg00116.html) )

---

### Post by boy18nj on 2013-04-18
> **sanderj said:**
> Q: why run chrome and not chromium?

I googled "comm: chrome-sandbox Tainted:" for you, and "google-chrome -no-sandbox" is suggested as work-around (see [http://lists.debian.org/debian-kernel/2010/09/msg00116.html](http://lists.debian.org/debian-kernel/2010/09/msg00116.html) )

thanks this confirms my suspicion the problem is with chrome. I'm not going to installing patches and all that. it should come as part of next released kernel distribution.

the reason i am using chrome because i do have some software which won't work in chromium.

---

