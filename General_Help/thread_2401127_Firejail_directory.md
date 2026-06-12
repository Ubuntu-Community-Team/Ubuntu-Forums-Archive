---
title: "Firejail directory"
date: 2018-09-13
forum: General Help
---

### Post by raleigh3 on 2018-09-13
At one time I had Firejail but I removed it.

I found a etc/firejail directory.

Can I remove it?

---

### Post by &amp;KyT$0P# on 2018-09-13
If you installed .deb package of firejail, it would be best to remove that directory with [FONT=Courier New]sudo apt-get purge firejail[/FONT] and/or [FONT=Courier New]sudo apt-get purge firejail-profiles[/FONT] .

---

### Post by Skaperen on 2018-09-13
_what's in it?_  i have no idea what _firejail_ is.  but, if it hooked your system with stuff it put in there, you could have problems.  what i would do in a case like this, if i didn't learn anything from a recursive listing of it (rather unlikely), is rename it so anything going to that name should fail (though i have written software that can't be tricked by that an find its stuff, anyway), reboot, and run the system for a day or two.  i'd also make a tarball or other backup of it, before removing it, just in case.

---

### Post by raleigh3 on 2018-09-14
thanks halogen2. That removed it.

---

