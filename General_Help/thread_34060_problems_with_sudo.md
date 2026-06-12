---
title: "problems with sudo"
date: 2005-05-13
forum: General Help
---

### Post by Ray Hamilton on 2005-05-13
It may be my newbie-ness but why is it that e.g. if I try something that requires sudo and its password from a menu e.g. firestarter, I get an invalid password message.  If though I start a terminal sessions and type e.g. sudo firestarted, the same password is accepted.  I have tried this several times and it is not the fact that I am typing a different password.

The same applies with xsane, in fact I got it working once, but now it reports that there is no device, one cause of which is invalid permissions.  Is this related to my sudo problems (they are not pseudo problems!) 

Help, I am finding this really frustrating - I even had a problem with adding a new user.

---

### Post by codejunkie on 2005-05-13
did you do a default install or expert install? the same thing happened to me when i did a expert install and enabled shadow passwords and entered the root password
every thing form the menu was messed but sudo still worked from the terminal.

---

### Post by Ray Hamilton on 2005-05-13
I did a default install as far as I remember.  I also seem to recall that it was the Kubuntu flavour, that I later added Gnome to.  But they are supposed to be the same apart from the interface/gui ?

---

### Post by Xian on 2005-05-13
[QUOTE=Ray Hamilton]It may be my newbie-ness but why is it that e.g. if I try something that requires sudo and its password from a menu e.g. firestarter, I get an invalid password message.  If though I start a terminal sessions and type e.g. sudo firestarted, the same password is accepted.  I have tried this several times and it is not the fact that I am typing a different password.[/QUOTE]
The same thing happens to me when I try to initiate a Firestarter session. Unless you also are unable to access other programs like synaptic from the menu, then I'd have to think the issue lies within the particular software package, or how it has configured itself to Ubuntu's sudo environment.

---

### Post by pointym5 on 2005-05-13
No, that doesn't make any sense.  Programs have no idea they're being executed under a "sudo" environment, *unless* they explicitly check for the difference between the real user ID and the effective user ID.  If that's the case, then the behavior would be the same from the command line or the GUI.

---

