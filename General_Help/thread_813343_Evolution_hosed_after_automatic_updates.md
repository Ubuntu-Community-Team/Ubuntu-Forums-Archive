---
title: "Evolution hosed after automatic updates"
date: 2008-05-30
forum: General Help
---

### Post by Dark Angel on 2008-05-30
I just let the automatic updates go through (literally about ten minutes ago) and something has hosed evolution.  I had a look and it's been uninstalled as part of the 'update'.

When I try to reinstall it I get:

> evolution:
  Depends: evolution-common (=2.22.1.1-0ubuntu3) but 2.22.2-0ubuntu1 is to be installed
 Depends: evolution-data-server but it is not going to be installed


Trying to install the data server component gives me:

> evolution-data-server:
  Depends: evolution-data-server-common (=2.22.1.1-0ubuntu3) but 2.22.2-0ubuntu1 is to be installed

Guys?  Please?  I kinda NEED all the email that's just been taken from me.

---

### Post by VMC on 2008-05-30
I just checked my Evolution and it is at 2.22.2
The only difference I notice was that now I need another password to enable send/rec.
I don't know about the data server issue.

That update was several days ago. The only current update was regarding the games suite.

---

### Post by Dark Angel on 2008-05-30
Ok, I'll change the server I'm using and see if that helps.  Maybe there's some mismatch between versions or something.

Like I said, the update that set this off only came in this morning local time.

-- Ok, updated the repos from the main server.  There's a temporary mismatch in versions that caused my system to remove evolution due to un-achievable dependencies.

---

### Post by Dark Angel on 2008-05-31
Ok, all better now. Thanks :)

---

