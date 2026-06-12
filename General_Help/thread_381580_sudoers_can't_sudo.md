---
title: "sudoers can't sudo"
date: 2007-03-11
forum: General Help
---

### Post by CocoAUS on 2007-03-11
I've added a user to the sudo file via System > Admin > Users and Groups, then double-checked in the /etc/groups file, and the user is listed as part of the adm group.  However, when the user tries to sudo, the terminal promptly (get it?) informs him that he is not a sudoer!  What's the deal?

---

### Post by jrib on 2007-03-11
> **CocoAUS said:**
> I've added a user to the sudo file via System > Admin > Users and Groups, then double-checked in the /etc/groups file, and the user is listed as part of the adm group.  However, when the user tries to sudo, the terminal promptly (get it?) informs him that he is not a sudoer!  What's the deal?

The group for sudo privileges is "admin" by default.  I'm not sure why the gui app didn't add your user to the correct group.

---

