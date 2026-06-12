---
title: "Another Sound Issue"
date: 2012-11-28
forum: General Help
---

### Post by raven2099 on 2012-11-28
I have a Toshiba Sat. L355-s7905 running 12.10 ubuntu...
when watching videos or listening to music the sound is a but quiet even though i maxed out the volume...

i tried installing the relteck stuff but to no avail
i tried installing a windows sound enhancer with wine.. bit it finds no codex or device...

any ideas?
suggestions?
tools?

---

### Post by dannyboy79 on 2012-11-28
have you insured volumes are at adequete levels in alsamixer?
open a terminal and issue 
```
alsamixer
```
and make sure all settings are maxed out. Have you installed pavucontrol also?

---

### Post by raven2099 on 2012-11-30
all maxed out now

---

### Post by dannyboy79 on 2012-11-30
and, did it fix your issue? Make sure they have 00 at the bottom and not MM, if it's MM, that means it's muted. Press M on the ones that have MM, and they'll turn to 00.

---

