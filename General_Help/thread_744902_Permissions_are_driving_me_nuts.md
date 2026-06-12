---
title: "Permissions are driving me nuts"
date: 2008-04-04
forum: General Help
---

### Post by jhyland87 on 2008-04-04
ok, so I asked before how to make it so the user I logon with has the same permissions and access to the same files as root. The solution I was given was to install some things and now I can rightclick on a program and select open as root. However.. that wont suffice... I cant save any files made in photoshop to the www folder, I cant run some programs with wine doors, I cant play some games... How can I make it so the roots folder is 100% open to my user account?

---

### Post by sekinto on 2008-04-04
Open nautilus: gksudo nautilus
Right click root's folder and click preferences.
Go to permissions tab and give your group read and write and access and delete permissions.
Click: apply permissions to enclosed files

Although I'm not sure how safe that is.

---

### Post by jocko on 2008-04-04
> **sekinto said:**
> Open nautilus: gksudo nautilus
Right click root's folder and click preferences.
Go to permissions tab and give your group read and write and access and delete permissions.
Click: apply permissions to enclosed files

Although I'm not sure how safe that is.

That's probably VERY unsafe.

---

### Post by sekinto on 2008-04-04
> **jocko said:**
> That's probably VERY unsafe.

I thought so, but the question the OP is asking doesn't really have a safe answer.

---

### Post by jocko on 2008-04-04
> **sekinto said:**
> I thought so, but the question the OP is asking doesn't really have a safe answer.

The *safe* answer is: A user should *never* have read-write permissions to any directory normally owned by root. Changing permission on the wrong file or folder (like everything in /) will make the system completely unusable and force a complete reinstall.

Save the files somewhere else (i.e a folder in your home directory or a monted drive you have permissions to).

---

### Post by HereInOz on 2008-04-04
Why not use 

gksudo nautilus

in a terminal to open Nautilus with root permissions when you want to copy files to the www folder, then when Nautilus is closed, the root permissions are lost until the next time.

You don't need to change permissions on anything at any time - just use the above command when you need it, and only when you need it, then close Nautilus once you have finished with it.

---

### Post by jhyland87 on 2008-04-04
why is it so unsafe and unsecure for the owner of root... to share the permissions of root with his other account... all it would be is like a gui version of root. 

Maybe I should just change the location of the WWW  and HTML folders...

---

