---
title: "Gnome- no system sounds:  fixed"
date: 2008-04-26
forum: General Help
---

### Post by aquaboot on 2008-04-26
Hi All,

I've been struggling with an irritating issue.  All sound works on gnome 2.22.1 except system event sounds.  With a little help from pulseaudio.org I fixed the problem and all system event sounds now play.  Here's the simple fix:

[I]aptitude install pulseaudio-esound-compat
[/I]
checked /usr/bin/esd to make sure it was symlinked to esdcompat- it was.

Rebooted and voila! All system sounds now play.

Cheers, 

ab

---

### Post by j_baer on 2008-04-26
aquaboot,

Are you getting the logout sound. This worked for me until RC.

Thanks,

John

---

### Post by aquaboot on 2008-04-27
Well... everything but logout.  This is also an issue on my Debian *testing* release, and freebsd machines.  EVERYTHING BUT LOGOUT- damn this is a stubborn problem.

-ab

---

