---
title: "No crash report notifications"
date: 2007-10-19
forum: General Help
---

### Post by chrisccoulson on 2007-10-19
Apport is not notifying me of new crash reports. Compiz crashes freiquently on my system with no notification, and when I looked in /var/crash, there are crash reports from other applications that I've never been notified about.

Running /usr/share/apport/apport-checkreports in a terminal does nothing.

However, when I ran /usr/share/apport/apport-gtk, I was immediately presented with a string of Apport notifications in succession, due to the crash reports already stored in /var/crash. I get the same behaviour with every user. There is only one entry in /etc/apport/blacklist.d
, and that is '/usr/bin/wine-preloader'.

Am I not meant to be notified of new crash reports?

This is on Gutsy

---

### Post by heikkitoivonen on 2007-10-21
I am in the same boat here. The crash tool worked great using the LiveCD, but hasn't worked after real install.

---

### Post by chrisccoulson on 2007-10-22
I will open up a bug report once I get home from work later

---

### Post by chrisccoulson on 2007-10-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/apport/+bug/155884](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/155884) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Would you mind commenting on the bug report?

Cheers

---

