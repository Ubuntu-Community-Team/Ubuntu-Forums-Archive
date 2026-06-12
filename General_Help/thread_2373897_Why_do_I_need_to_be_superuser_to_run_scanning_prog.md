---
title: "Why do I need to be superuser to run scanning program?"
date: 2017-10-10
forum: General Help
---

### Post by dces on 2017-10-10
Hi

I am running ubuntu 17.04 with a Brother printer/copier/scanner attached to my HP laptop.

To enable scanning I installed the simple scan program. However, when I try to scan by either clicking the desktop icon, or entering simple-scan in the Terminal, I get a "Failed to scan - unable to connect to scanner" message. But, if I enter gksudo simple-scan in the Terminal, scanning works perfectly. What settings/permissions do I need to change?

Cheers
Dave

---

### Post by deadflowr on 2017-10-10
Seems like you're running in a similar issue as this:
[https://ubuntuforums.org/showthread.php?t=2265154]("https://ubuntuforums.org/showthread.php?t=2265154")

---

### Post by dces on 2017-10-11
Thanks for the pointer. Seems like I need to chmod some settings, leave it with me.

Cheers
Dave

---

### Post by dces on 2018-01-28
Now solved.
Upgraded to 17.10, removed the printer from the os, reinstalled the printer, downloaded the printer/scanner drivers again and ran the driver installation tool from the Brother website. Simple Scan now works.

Dave

---

