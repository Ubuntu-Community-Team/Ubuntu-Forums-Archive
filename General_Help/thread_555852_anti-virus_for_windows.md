---
title: "anti-virus for windows"
date: 2007-09-20
forum: General Help
---

### Post by Valkyrie Wrath on 2007-09-20
are there any anti-virus program for Ubuntu that will catch viruses on Windows? I just need one because my Windows desktop is acting up.

---

### Post by Steveway on 2007-09-20
Most if not all anti-virus programs wich work on Linux scan for Windows-virii.
Try ClamAV, it is one of the best.

---

### Post by Valkyrie Wrath on 2007-09-20
"You do not appear to have virus definitions!

Running "freshclam -v" as root may fix the problem."

I got this message when I hit scan. Am I supposed to enter that in the terminal or something?

---

### Post by tszanon on 2007-09-20
There's also avast for linux. Free for home use.

---

### Post by Valkyrie Wrath on 2007-09-20
Why does it give me that message?

---

### Post by Sef on 2007-09-20
How did you download clamav?

---

### Post by benx009 on 2007-09-20
> **Valkyrie Wrath said:**
> "You do not appear to have virus definitions!

Running "freshclam -v" as root may fix the problem."

I got this message when I hit scan. Am I supposed to enter that in the terminal or something?

um, are you running the command as root?

do "sudo su" in a terminal, type in the root password (probably just your regular password, if you're not sure), and then try the command again.

---

### Post by Valkyrie Wrath on 2007-09-20
When I put it in the terminal I got this message

"root@ubuntu:/home/sean# freshclam -v
Current working dir is /var/lib/clamav/
Max retries == 5
ClamAV update process started at Thu Sep 20 19:05:23 2007
Querying current.cvd.clamav.net
TTL: 135
Software version from DNS: 0.91.2
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.90.2 Recommended version: 0.91.2
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
main.cvd version from DNS: 44
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.cvd version from DNS: 4355
daily.inc is up to date (version: 4355, sigs: 21544, f-level: 21, builder: ccordes)"

---

### Post by Maestro23 on 2007-09-20
> **Valkyrie Wrath said:**
> When I put it in the terminal I got this message

"root@ubuntu:/home/sean# freshclam -v
Current working dir is /var/lib/clamav/
Max retries == 5
ClamAV update process started at Thu Sep 20 19:05:23 2007
Querying current.cvd.clamav.net
TTL: 135
Software version from DNS: 0.91.2
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.90.2 Recommended version: 0.91.2
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
main.cvd version from DNS: 44
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.cvd version from DNS: 4355
daily.inc is up to date (version: 4355, sigs: 21544, f-level: 21, builder: ccordes)"

When in doubt, do what it says.  FAQ: [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)

---

