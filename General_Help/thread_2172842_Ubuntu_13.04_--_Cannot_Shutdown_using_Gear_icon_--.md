---
title: "Ubuntu 13.04 -- Cannot Shutdown using Gear icon --- Shutdown button"
date: 2013-09-06
forum: General Help
---

### Post by blake4 on 2013-09-06
I can't shut down the computer. I click shutdown, by computer continues to stay awake and I can still continue to do what I'm doing. Also,

Shutdown -h doesn't work either. Besides holding down the physical power button, I cannot shut down. Not that I do often anyway, but it's an important thing for a computer to have.

---

### Post by bkline on 2013-09-07
You might want to look in /var/log/syslog so see if there are any clues about what's preventing a shutdown (I assume you're running it as root and giving it the "now" argument).  Also, there's a safer way to shut down a Linux system than shutting off the power, even when shutdown doesn't work.  Details at:

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

