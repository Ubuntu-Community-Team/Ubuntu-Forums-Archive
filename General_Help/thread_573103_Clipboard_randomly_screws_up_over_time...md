---
title: "Clipboard randomly screws up over time.."
date: 2007-10-11
forum: General Help
---

### Post by Naatan on 2007-10-11
Hi, for the past 3 days I've had my clipboard screwing up randomly over time, meaning that at some point it just stops working and when I copy/paste something it always pastes the following:

ŸŸ

Sometimes it pastes code a bit different from that but it always contains the two "ŸŸ"

This is EXTREMELY annoying as it forces me to restart X every time it does this, since I haven't found a better solution so far.

Does anyone know what might cause this?

Note, im using Synergy2 between two Ubuntu installations (both Gutsy), Synergy shares clipboards between computers, but the problem only occurs on one of the computers (the client).

---

### Post by praet on 2007-10-11
Sounds like a known bug when using virtualbox.  Do you happen to have vbox running?

---

### Post by Naatan on 2007-10-12
I do actually, though not all the time..

Glad to hear I'm not the only one.. is there a fix (planned) ?

---

### Post by praet on 2007-10-12
I'm glad you identified the problem.
Yes it has already been fixed as of virtualbox 1.5.2 as per this ticket:
[http://www.virtualbox.org/ticket/611](http://www.virtualbox.org/ticket/611)

It is caused by the bi-directional clipboard feature.  So if you cant wait for the update release, change the shared clipboard from bi-directional to "Host to Guest" for a more stable clipboard.

---

### Post by Naatan on 2007-10-12
Awesome, thanks mate!

---

