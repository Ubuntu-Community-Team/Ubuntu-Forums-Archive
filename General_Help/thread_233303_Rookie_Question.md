---
title: "Rookie Question"
date: 2006-08-09
forum: General Help
---

### Post by l.j. on 2006-08-09
I installed a program dosent agree with my system no big deal, but i see no uninstaller how does one cleanly remove a program, or does it send files everwhere like a windows installation ie is thier a registry etc. sorry this is prob a dumb question but thanx for any help:D

---

### Post by djSeverin on 2006-08-09
Hi l.j. It depends how exactly you installed the program. Was it a DEB package, or an RPM, or a tarball?

Would you please post the name of the program, the name of the file that actually performed the install, and the steps you followed to install it? :-)

---

### Post by l.j. on 2006-08-10
Thanx for the reply in was wolfenstein mpdemo it was a .run file from the command as root thanx again

---

### Post by djSeverin on 2006-08-12
Ok. Unlike a deb or an rpm, ".run" files can't be automatically removed from your system.

On the up-side, these files "generally" install their content to a single location. I would suggest using the search tool (or "locate wolfmpdemo" at a console) to find where the installer put everything (use the keyword "wolfmpdemo"). My guess would be "/usr/something".

Once you find the demo's location, its simply a case of removing it.

---

