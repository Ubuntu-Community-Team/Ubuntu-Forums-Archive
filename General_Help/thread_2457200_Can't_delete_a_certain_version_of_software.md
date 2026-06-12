---
title: "Can't delete a certain version of software"
date: 2021-01-27
forum: General Help
---

### Post by jmichaels29 on 2021-01-27
I've tried to delete the version of "skanlite" on my system.  Tried purging it, removing it in synaptic, and removing it using Ubuntu software center (synaptic and software center won't recognize that its' installed).

If I install "skanlite" from ubuntu software or synaptic, it installs a 2nd version in my applications (a 2nd version that actually works).  I end up with 2 identical images of Skanlite in my applications.

I temporarily deleted the 2nd version that works, so that perhaps someone could help me delete the 1st version (it opens but won't find my scanner like the 2nd version did).

---

### Post by Holger_Gehrke on 2021-01-27
If synaptic doesn't see it, then it could be a snap package (although Ubuntu Software should see those ...). Enter 'snap list' in a terminal to verify that that's what it is. 'snap remove "*exact name as shown by list*"' should remove it. If it is a snap, then there's probably some interface you need to give the snap access to ("snap connect 'name of snap':'name of plug'") to allow it to see your scanner.

Holger

---

### Post by jmichaels29 on 2021-01-27
ok, that removed it, thanks!

michael@michael-HP-EliteDesk-800-G1-SFF:~$ snap find skanlite
Name      Version         Publisher  Notes  Summary
skanlite  master+cb382f8  kde&#10003;       -      image scanner based on the KSane backend
michael@michael-HP-EliteDesk-800-G1-SFF:~$ snap remove skanlite
skanlite removed
michael@michael-HP-EliteDesk-800-G1-SFF:~$

---

