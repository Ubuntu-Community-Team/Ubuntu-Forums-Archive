---
title: "Dosemu broken in Wily  - stack smashed"
date: 2016-01-28
forum: General Help
---

### Post by mjacek8 on 2016-01-28
Dosemu (DOS emulator) seems to be broken in Wily. 

Running any DJGPP program ends in *** stack smashed ***  message and dosemu is killed. 
I haven't tried other programs, as all I have is a DJGPP Gnu C compiler for maintaining old-old-dos software running on some old-old hardware.

Temporarily resolved this by installing a dosemu package from Trusty, which runs smoothly.

Setup:
Wily Werewolf (amd64) Dell Latitude laptop with i5-3340M and optimus video (used in intel-only mode)
first broken:    dosemu_1.4.0.7+20130105+b028d3f-2_amd64.deb
latest running: dosemu_1.4.0.7+20130105+b028d3f-1_amd64.deb

---

