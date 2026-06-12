---
title: "How can I remove wine's menu entries?"
date: 2007-04-23
forum: General Help
---

### Post by Vinze on 2007-04-23
Hi, I installed a program with Wine. After finding out that it didn't work I decided to uninstall the program, which went fine, apart from the fact that all menu entries remained. This is the case for every program I install with Wine and for all versions of Ubuntu I've tried up till now. How can I remove these menu entries?

Thanks in advance.

---

### Post by orb9220 on 2007-04-23
Goto Systems>Preferences>Main Menu  and then just  un-check ones to not show in menu.

---

### Post by Vinze on 2007-04-23
O, sorry, I forgot to tell I'm on Xubuntu, I need to find where wine stores the .desktop files.

---

### Post by pangos on 2007-04-28
Hi, the desktop icons stored for wine can be found in 
~/.wine/Windows/Profiles/<username>/Desktop.

Similarly the Start Menu icons should be in
~/.wine/Windows/Profiles/<username>/Start Menu

Cheers

PangOS

---

### Post by Vinze on 2007-04-28
> **pangos said:**
> Hi, the desktop icons stored for wine can be found in 
~/.wine/Windows/Profiles/<username>/Desktop.

Similarly the Start Menu icons should be in
~/.wine/Windows/Profiles/<username>/Start Menu

Cheers

PangOS

Weird, cause I already had found it to be in ~/.local/applications/blabla or something like that.

---

### Post by ashz on 2007-04-28
stick to what u know!!

---

### Post by !@!@! on 2008-06-27
System>Pref>Main Menu
then go to wine, make the menu drop down if it isnt,
then just  right click on what you want gone and hit delete.
wah la.
:guitar:

---

