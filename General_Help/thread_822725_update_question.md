---
title: "update question"
date: 2008-06-08
forum: General Help
---

### Post by King Buttons I on 2008-06-08
I unistalled the version of OpenOffice.org that came with Ubuntu and installed the one from the the OpenOffice.org website. Now the update manager is trying to install OOo updates. I was wondering if it was possible to disable those updates or would running the updates harm the system?
Buttons

---

### Post by housam on 2008-06-08
you can disable these updates by unchecking them in the update manager window.

---

### Post by King Buttons I on 2008-06-08
Is there a way to disable them permanently?

---

### Post by Anduu on 2008-06-08
gah nevermind posted before my brain kicked in :o

---

### Post by Anduu on 2008-06-08
Go into synaptic and select the version of Openoffice you have installed...it will probably be under "local/obsolete"

Then go to the Package menu and select lock version.

---

### Post by King Buttons I on 2008-06-09
Anduu
I did what you said and reloaded the update sources and the OOo updates still appear in there.
Buttons

---

### Post by cdtech on 2008-06-09
You need to sudo apt-get autoremove or sudo apt-get clean (should do this after removal, but you can still do it now). Also check your synaptic package manager and delete the residual config under status.

Hope this helps.....

---

