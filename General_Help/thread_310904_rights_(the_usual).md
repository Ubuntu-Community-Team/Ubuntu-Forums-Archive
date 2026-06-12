---
title: "rights (the usual)"
date: 2006-12-02
forum: General Help
---

### Post by pentium on 2006-12-02
I constaantly shoved this aside but after I started having problems compiling my Apollo Guidance Computer emulator, I finally got fed up.

I want to get _all_ root rights. From looking at passwd.pwd to deleting files made by other users.
What do I do?

---

### Post by ciscosurfer on 2006-12-02
You can setup a root account if you're in Dapper by following this guide (but be forewarned...this is not the way you're supposed to do things): [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) (go to the section marked "Going back to a traditional root account"

---

### Post by pentium on 2006-12-02
> (but be forewarned...this is not the way you're supposed to do things)
As in i shold just use sudo for everything?

---

### Post by strabes on 2006-12-02
pentium: exactly. using a root account is dangerous because you can accidentally delete something critical. That is why viruses affect Window$ so much.

---

### Post by ciscosurfer on 2006-12-02
> **pentium said:**
> As in i shold just use sudo for everything?Sudo sessions will last 15 minutes in the terminal.  You can modify this time, too.  But, yes.  You really shouldn't enable or use your root account carte blanche, or willy nilly, if you will. ;)

---

### Post by pentium on 2006-12-02
I understand that everything is locked for a reason but sometimes it prevents me from performing the most simplest of tasks like deleting an empty folder or moving a file around. Even with a sudo timer on the terminal, I kinda find it nice to click-and-drag but that requires file browser to be opened under root rights and if I want to delete a file that was made by oot that's in the trash, I need to sudo that too.
I have several files to move, I can't move them because one folder was made by root.

---

### Post by aysiu on 2006-12-02
You can drag an drop. Read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by pentium on 2006-12-02
I can work with that.
Thanks.:D

---

