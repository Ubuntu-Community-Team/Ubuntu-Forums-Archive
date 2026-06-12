---
title: "Unable to edit Samba"
date: 2005-08-08
forum: General Help
---

### Post by N8MAN1068 on 2005-08-08
KDE 3.4.2
Going into Preferences-Control Center-Samba.
I click on Samba, everything is greyed out...Click on Administrator Mode...it asks for my pw..enter pw...sits @loading for a second or two, and then brings up the KDE Control Center screen...

Whats up with that?
Anyone ever have that happen or know how to get around that?

---

### Post by eivind on 2005-08-08
First: Is samba installed? It may not be, even though the kde control center module is visible. Try 

sudo apt-get install samba 

in a console, just to be sure. This command won't hurt, if samba is installed already, it will simply do nothing.

Cheers,

Eivind

---

### Post by N8MAN1068 on 2005-08-08
yup.
samba+samba common+python2.4-samba, all 3.0.10-1ubuntu3

i coulda swore it work before i upgraded to kde 3.4.2
not entirely sure though. ](*,)

---

### Post by kenj on 2005-08-08
I had the same problem with Administrator Mode.
Go to the menu and click "RUN Command"
Enter "kdesu kcontrol" (no quotes).
It will then ask for your password.
Enter your password and kcontrol should come up in administrator mode.
I don't know why the Administrator Mode button doesn't work, but this worked for me.
Good luck!

---

### Post by N8MAN1068 on 2005-08-08
seems to do it.
interesting...

---

### Post by Takis on 2005-08-09
Yeah KControl has some weird bug that they haven't been able to fix yet. It's reasonably complicated because it actually pulls up a second window (a new program) and "docks" it into the Control Centre window you already have open.

My workaround for this bug is to have a second copy of the Control Centre shortcut in my KMenu. It's an exact copy of the original, just in the properties I've set it to run as a different user (if you don't specify which user, it assumes root). This works just fine.

---

### Post by LadFromWales85 on 2008-03-18
Has this bug been fixed yet?  As I'm experiencing the same problem with Feisty / KDE 3.5.8!

---

