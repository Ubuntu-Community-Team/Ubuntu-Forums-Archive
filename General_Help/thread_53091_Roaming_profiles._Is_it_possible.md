---
title: "Roaming profiles. Is it possible?"
date: 2005-07-30
forum: General Help
---

### Post by navilon on 2005-07-30
Ok, here is what i would like to do:

I have 5 linux desktops and one linux server. I would like to be able to have accounts set up on the server so that no matter which computer i log into (preferably through GDM, i would have the same settings, home folder, etc.

So basicly something like romaing profiles on windows.

is this possible in linux?

---

### Post by adwait on 2005-07-30
I guess you could have your home partition stored on the server, and mount it as a network drive. The home partition stores all your personal settings, so I guess that should do the trick......

---

### Post by navilon on 2005-07-30
[QUOTE=adwait]I guess you could have your home partition stored on the server, and mount it as a network drive. The home partition stores all your personal settings, so I guess that should do the trick......[/QUOTE]
 thats true, but if i had 10 accounts and 10 workstations i would have to do it 100 times, thers got to be another way

can this be done with OpenLDAP or somethign else?

---

### Post by adwait on 2005-07-31
I don't understand......

When you install the OS on each workstation, you would have to speciffy the location for /home...so instead of specifying a local drive, you specify the network one. Wheres the difference?

---

### Post by kosmic on 2005-07-31
search for NIS and NFS, it can do what you want

---

