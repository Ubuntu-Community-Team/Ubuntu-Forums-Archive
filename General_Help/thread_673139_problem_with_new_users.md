---
title: "problem with new users"
date: 2008-01-20
forum: General Help
---

### Post by tech.roberts on 2008-01-20
I have added a new users using both the adduser command and the GUI.  In all cases the account is created with a home directory.  I can log in as the use, run applications, etc. so all seems well.  However there are two problems:  1)  the shutdown button does not work, i.e. can't get the dialog box offering logout, restart, etc.  2) all windows have no grab bar nor is there a minimize, maximize or shutdown button.  Basically all windows open in the top right corner of the screen with nothing above the menu bar.

I have tried creating superusers, regular users, etc.  My account works fine but any account I create has the problems described above.

Suggestions?

---

### Post by harlan on 2008-01-20
To fix the 2nd problem:
Applications-->System Tools-->ConfEditor and select desktop-->applications-->window manager
and select /usr/bin/metacity in default

---

### Post by tech.roberts on 2008-01-20
Following harlan's suggestion I find that /usr/bin/metacity is already set as the default.  Problem still unresolved.

---

### Post by tech.roberts on 2008-01-20
My thanks and apologies to harlan.  Your suggestion fixed both problems.   I was checking the configuration editor while logged into my account which was of course OK.  When I logged into the new user accounts I found the window manager was set a /usr/bin/compiz.  Changing this per your suggestion solved both issues.

---

