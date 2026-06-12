---
title: "&quot;Users and Groups&quot; greyed out - not usable"
date: 2008-05-06
forum: General Help
---

### Post by Endolith on 2008-05-06
I am trying to add a user using the GNOME "Users and Groups" tool, but it won't let me.  The "Add user" button is greyed out.  Apparently this has changed in Hardy Heron and I'm supposed to click the "Unlock" button first, but the "Unlock" button is greyed out, too.

---

### Post by chrisccoulson on 2008-05-06
What messages do you see if you run users-admin from the terminal?

---

### Post by Endolith on 2008-05-06
> **chrisccoulson said:**
> What messages do you see if you run users-admin from the terminal?

```
** (users-admin:24390): CRITICAL **: Unable to lookup session information for process '24390'

```

You know what, though?  I'm accessing this through NX, so that might be the problem.  I know it screws up the GNOME session and does weird things with processes running twice at the same time, for instance.

---

### Post by Endolith on 2008-05-06
Seems like that was the problem.  The Unlock button works fine locally.

---

### Post by formerwindowspoweruser on 2008-12-28
Another option, for those of use logged in locally, is to log out, then change the session to "FAILSAFE gnome." Logging in, the "unlock" for Users and groups was no longer grayed out. After making the changes I wanted, I logged out and set default session back to regular Gnome.

---

