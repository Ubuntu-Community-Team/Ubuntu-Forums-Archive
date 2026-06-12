---
title: "Boinc on 64bit OS"
date: 2006-08-21
forum: General Help
---

### Post by ngdias on 2006-08-21
I tried 3 BOINC projects so far - Seti, climateprediction and Einstein and all report the same problem:

Message from server: platform 'x86_64-pc-linux-gnu' not found

Is this happening to anyone else? Does anyone know a BOINC project that works on 64bit Linux?

---

### Post by psyncho on 2006-09-12
First, if you installed through aptitude then boinc should be running as a daemon and connecting using boinc_cmd (and though I'm having the same problem I don't get that message unless trying to run boinc client directly).

The actual command is:
boinc_cmd --project_attach url key

But yes, there are problems with 64 bit machines.  Climate prediction and einstein both say they support them. I found this one post on einstein project:
[http://einstein.phys.uwm.edu/forum_thread.php?id=4522](http://einstein.phys.uwm.edu/forum_thread.php?id=4522)

for getting 64 bit client running with it. 

I'm trying climate prediction right now through the isntall from the package, and if that doesn't work, then I'll have to try one of these custom isntalls from the sites using their 64 bit packages.  

Let me know if you manage to get it working and what you've done, and I'll do the same.

John

---

