---
title: "Problem with konsole, yakuake"
date: 2006-08-16
forum: General Help
---

### Post by smileyjon on 2006-08-16
Hi,

On a fresh install of Xubuntu 6.06, I used Synaptic to install yakuake and all of its dependencies. However it failed to start, and I tracked the underlying cause down to a problem with Konsole.

When I try and start Konsole I get an error dialogue saying:

> "Konsole is unable to open a PTY (pseudo teletype). It is likely that this is due to an incorrect configuration of the PTY devices. Konsole needs to have read/write access to the PTY devices."

and if I launch it from an xterm I also get written out to stderr:

> kbuildsycoca running...
konsole: WARNING: Unable to open a pseudo teletype!
Uh oh.. can't get terminal attributes..

I've checked /dev/pty* and they're all readable and writable by everyone. 

If I run konsole -e /bin/bash everything works fine.

Any ideas?

Thanks

j.

---

### Post by smileyjon on 2006-08-18
Silly me. I had my SHELL environment variable pointing to a location that didn't exist. All working now.

j.

---

