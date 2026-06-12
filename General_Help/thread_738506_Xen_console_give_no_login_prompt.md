---
title: "Xen console give no login prompt"
date: 2008-03-28
forum: General Help
---

### Post by mgoldsby on 2008-03-28
I'm running gutsy as dom0 and as domU.

'xm create etc.cfg -c' seems to boot the domU system ok, but 'xm console <id>' just responds with blank lines when I hit Enter.
  
It's not until I do 'xm shutdown <id>' that the login prompt appears (and by then it's too late, of course).

In my config file I have extra = "xencons=xvc0 console=xvc0"

Anyone out there have any ideas?

---

