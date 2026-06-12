---
title: "Declined: &quot;Oracle Binary Code License for Java&quot;"
date: 2014-02-17
forum: General Help
---

### Post by StevenD on 2014-02-17
There is one item in the Update Manager window that will not update and continues to fail.

Oracle Java(TM) Development Kit (JDK) 7
oracle-java7-installer (Size: 18 kB)

The message says:

Declined: "Oracle Binary Code License for Java"
If you do not agree to the license terms you cannot install this software.
The installation of this package will be canceled.

There is nothing for me to agree to. I am trying to figure out how to get rid of it so they don't show up in the Update Manager.

A while back I tried to set up I think it was Eclipse to go through some tutorials in a book on Android app development. I never could get things set up correctly so I gave up. Now I get these things that fail every time I try to update software from the Update Manager.

---

### Post by buzzingrobot on 2014-02-17
Eclipse is a (large) Java app, so perhaps things went awry then. Try deleting it and the Oracle Java as well.  You can find them in Software Center or Synaptic, assuming you installed them from .deb files.  Preferably Synaptic because it will offer to show you everything that will be removed. You want to look at it to be sure nothing you want to keep is on the list.


If you need Oracle Java, reinstall it and watch closely for that licensing panel.

---

