---
title: "is wubi compatible with windows xp media center edition?"
date: 2007-09-09
forum: General Help
---

### Post by rafaelm on 2007-09-09
so, i tried installing wubi on my windows xp media center edition 2002, and the setup file just won't open. i can see on the task manager that the process (Wubi-7.04.04.exe) appears and then suddenly disappears, so the setup file won't open. is this because wubi is not compatible with xp media center? thanks.

---

### Post by tripokey on 2007-09-09
There is a high probability that your wubi file is corrupted. Redownload it and try again.

---

### Post by rafaelm on 2007-09-09
i've tried that, it still doesn't work.

---

### Post by ago on 2007-09-09
> **rafaelm said:**
> so, i tried installing wubi on my windows xp media center edition 2002, and the setup file just won't open. i can see on the task manager that the process (Wubi-7.04.04.exe) appears and then suddenly disappears, so the setup file won't open. is this because wubi is not compatible with xp media center? thanks.

Hmm not sure, non of the devs has wmc that I am aware of. We'd need some more info, but I'd tend to guess that it should not make much difference.

---

### Post by Romanus81 on 2007-09-10
I got it to work on my MCE 2005, it should work on 2002, do you think it could be a firewall or something?

---

### Post by lituus on 2007-09-16
> **rafaelm said:**
> so, i tried installing wubi on my windows xp media center edition 2002, and the setup file just won't open. i can see on the task manager that the process (Wubi-7.04.04.exe) appears and then suddenly disappears, so the setup file won't open. is this because wubi is not compatible with xp media center? thanks.
try multiple things:

redownload

click save instead  of open/run at the dload dialog, then run from dektop

rt.click the installer, click "unblock"

turn off DEP/add an exception via rt.click "My Computer">Properties>Advanced>DEP

run an MD5 check on the file

check to see if "mDNSresponder.exe" is running in Task Manager>Processes, this is run by BonjourCore on startup (in case you are using iTunes+iPod, or Ruckus. This causes loadsa problems

dload with Firefox [this actually works sometimes when IE7 doesn't]

run Spybot and CCleaner checks on ur machine. get rid of crap. [pr0n too]

upgrade to XPMCE 2005.

post a HijackThis log.

format and install Ubuntu!!

---

