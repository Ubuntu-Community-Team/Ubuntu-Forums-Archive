---
title: "[SOLVED] CD (iso-8859-15) refuses to install (utf8 gutsy)"
date: 2007-10-30
forum: General Help
---

### Post by soxs on 2007-10-30
The cd is called "Generäle" and is win game (they so dumb naming a game with special chars -.-)
So the game would work fine (app.db winehq.org), but it does not find the installer msi data as it searches for "*ä*" but Ubuntu names it "*?*" (? with black background, the unknown char thing or something)
So my question: can I moun ta cd with a diffrent char set to display names correctly so I can install it just like the GB/US version?

---

### Post by soxs on 2007-11-02
Solution: set the iocharset in /etc/fstab to 8859-15 (or whatever your locale is)
e.g:
/dev/scd1 /media/cdrom0 udf,iso9660 iocharset=iso8859-15,user,noauto 0 0

---

