---
title: "After 12/05/18 update to 18.04 some pdf files won't open"
date: 2018-12-05
forum: General Help
---

### Post by lou6 on 2018-12-05
Title says it all - did software update this a.m. - now some (not all) pdf files won't open.  Both pdf viewers are affected (qpdfview, evince).

Help or commiseration appreciated...

---

### Post by Impavidus on 2018-12-05
I've seen some upgrades to libpoppler in recent days, which may have caused the issue. It could be a bug. Both evince and qpdfview depend on libpoppler.

There are pdf viewers that don't depend on libpoppler, like gv, which uses ghostscript. That may still work.

---

### Post by lou6 on 2018-12-05
Thanks for the prompt reply - I'm hoping that my post will encourage whoever broke it to (please) fix it :)

I'm extremely happy with qpdfview (and have never had much success installing things like gv that need to be "made")

UPDATE - Thanks Impavidus - I didn't realize that gv could be installed from repos and did not require a make.  It will hold me over nicely until libpoppler is fixed.

---

### Post by Impavidus on 2018-12-06
See [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

If you can provide the devs with some useful information, that may help fix this. Maybe someone has already reported this problem.

---

### Post by lou6 on 2018-12-06
A good idea but I think it will take someone with a bit more Linux experience (semi-noob here) to prepare a cogent apport submission.  All I've been able to determine is that "some" pdf files terminate with a segfault which "may" be caused by poppler and affects "at least" two pdf readers - pretty circumstantial but possibly a good clue.

Not that I don't want to help but the process seems somewhat beyond my abilities.

Thanks again for replying.  I'll leave this post open for now and see if others are having the same problem.

---

### Post by lou6 on 2018-12-08
Closing this due to lack of further responses though it is NOT solved...

UPDATE:  After closing this earlier I decided to bite the bullet and file a Launchpad bug report.  Not as difficult to do as I thought.  

If you are having this problem (PDFs that used to open but now do not) please go to
 
[https://bugs.launchpad.net/ubuntu/+source/poppler/+bug/1807504](https://bugs.launchpad.net/ubuntu/+source/poppler/+bug/1807504) 

and add yourself to the list

---

### Post by lou6 on 2018-12-11
Fixed today.  I will mark this as closed.

---

### Post by QIII on 2018-12-11
Would you care to share the solution with the community so that the next person doesn't have to struggle to find the answer?

The UF exists for the benefit of the whole community.

Thanks!

---

### Post by ajgreeny on 2018-12-11
QIII, it was a regression in the libpoppler73 version which upgraded today from 0.62.0-2ubuntu2.4 to 0.62.0-2ubuntu2.5, the new version arrived in normal upgrades, so anyone else with the problem should find that it is solved simply by keeping their system updated.

See [https://usn.ubuntu.com/3837-2/](https://usn.ubuntu.com/3837-2/)

---

