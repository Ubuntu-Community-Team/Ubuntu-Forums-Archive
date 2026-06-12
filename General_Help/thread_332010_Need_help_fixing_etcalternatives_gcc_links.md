---
title: "Need help fixing /etc/alternatives gcc links"
date: 2007-01-05
forum: General Help
---

### Post by Njall on 2007-01-05
I did a baaaaad thing the other day.  I am a complete /etc/alternatives noob.   At the time I was building a package which needed gcc 3.4.  Not knowing anything about /etc/alternatives I manually changed the symlink in /usr/bin/cc to point directly to gcc-3.4.   I have both gcc-3.4 and 4.1 installed.  Apparently I also removed, though this I don't recall this, any /etc/alternatives/cc and/or .../gcc entries.  I'd like to correct my mistake(s).

Poking around I found galternatives.  However, it apparently only works on existing /etc/alternative entries.  Using update-alternatives is not immediately obvious.  How do I go about restoring the /etc/alternative entries for both gcc-3.4 and gcc-4.1 so that, next time, I can use update-alternatives or galternatives to do it correctly?

BTW - I have already, as part of my attempt to resolve my incompetence, reinstalled both gcc-3.4 and gcc-4.1 hoping that the installation programs would fix my faux pax.   Alas, not.

Thank you for any help you might offer.

Nelson

---

