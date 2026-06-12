---
title: "OpenOffice fails on startup for some users"
date: 2008-02-07
forum: General Help
---

### Post by beazer on 2008-02-07
Hi

I'm getting failures of all OO applications (oowriter, oocalc, etc) for some users on an Ubuntu 7.10 machine, with OpenOffice 2.3 installed.

Users defined in /etc/passwd have no problems - all OO apps work perfectly.

Some of our users are being authenticated from a MS 2003 server using Active Directory through winbind. If they try to start any OO application (oowriter, oocalc, etc) they get the splash screen, followed by a dialog "The application cannot be started. An internal error occurred."

There are no other error indications or log messages.

We have tried removing the user's ~/.openoffice.org2 directories and they get re-created, just before the error message shows up again and OO fails.

Can anyone help with this problem?

Many thanks
Rob

---

