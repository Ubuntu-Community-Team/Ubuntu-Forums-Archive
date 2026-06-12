---
title: "qpdf view"
date: 2017-04-12
forum: General Help
---

### Post by cmcanulty on 2017-04-12
This is driving me nuts. Qpdf view, which I love keeps starting at boot on one xubuntu 16.04. It is not in session and startup-application autostart for either user. I also looked in /etc/xdg/autostart. It also isn't in .config/autostart for either user. I even tried completely remove and reinstall and the behavior persisted.  Is there anywhere else I can eliminate this from? Thanks

---

### Post by ajgreeny on 2017-04-12
Have you at some point saved a session at shutdown of the session when it was running?

Have a look in ~/.cache/sessions for any files starting with names starting xf, and remove them, then shutdown all running applications to a completely empty desktop, and finally shutdown the system, this time choosing to save the session for future use.

Hopefully that will have removed qpdfview from your startup applications.

Make sure that next time you shutdown the save session box **is not selected**.

---

### Post by cmcanulty on 2017-04-12
I did check that the session box is always unchecked. The library just shutdown at 5pm so I will try that tomorrow when they reopen. What does the xf in .cache refer to? Thank you.

---

### Post by ajgreeny on 2017-04-13
All the previous session files are named something such as .cache/sessions/**xfce4-session-XubuntuXenial:0** so my suggestion was to remove any files with that **xf** start to their name, rather than  looking for a specific named file.

---

### Post by cmcanulty on 2017-04-13
the .cache/sessions worked. thanks so much now I know for those irritating times when xfce keeps starting something up that isn't listed.

---

