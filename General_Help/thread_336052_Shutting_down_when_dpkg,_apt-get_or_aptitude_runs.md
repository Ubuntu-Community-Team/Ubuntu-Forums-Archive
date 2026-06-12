---
title: "Shutting down when dpkg, apt-get or aptitude runs"
date: 2007-01-11
forum: General Help
---

### Post by The Keeper on 2007-01-11
What happens when apt-get or aptitude is scheduled to run and is in progress of downloading or installing updates when an user decides to turn off the computer? Does dpkg prevent shutdown until it is finished?

If not, is there a reliable way to schedule updates to run at certain times in ubuntu boxes that are almost always used by non-sudoers? Who of course won't know when updates are being downloaded and installed.

---

### Post by Jussi Kukkonen on 2007-01-11
Killing the processes in download phase is not fatal, but you do have a point if "install security updates automatically" is in use... I've never used it so I don't know: does it really not even tell the user it's doing an update?

---

### Post by The Keeper on 2007-01-11
Interrupting apt-get during download phase should indeed be safe, but I am worried about when apt-get / dpkg is installing these updates. In worst case scenario if installation is interrupted prematurely and computer is turned off or restarted, it may even become unbootable.

Which is why I'd like to know if the update/upgrade process has a safe-guard against this.

---

