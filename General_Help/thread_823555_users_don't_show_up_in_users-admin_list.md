---
title: "users don't show up in users-admin list"
date: 2008-06-09
forum: General Help
---

### Post by os.getlogin on 2008-06-09
Hi.  I added a group (myname) and user (myname) with the following:
> 
$ sudo groupadd -g 555 myname
$ sudo useradd -u 555 -g 10 -d /etc/tsg myname


Two questions:
1. I think I should have used -u 555 -g 555 to put user myname into group myname.  What did the above actually do with the user-group relationship?
2. When I open users-admin, the myname user does not show up, but the myname group does.  Any ideas here?

Nate

---

### Post by Habbit on 2008-06-09
This is only a theory, but I think that users-admin only shows users with uid > 1000, as normal programs create users (unless overriden like you did) with those ids, and reserve the low numbers for system and daemon accounts. Have you tried with another UID?

Regarding your first question, I think the answer is yes. Most probably the system did not spit an error because group #10 already exists (in my box, it is group "uucp").

---

### Post by os.getlogin on 2008-06-09
> This is only a theory, but I think that users-admin only shows users with uid > 1000, as normal programs create users (unless overriden like you did) with those ids, and reserve the low numbers for system and daemon accounts. Have you tried with another UID?

Ok, I think this helps.  I changed UID_MIN in /etc/login.defs to 100 and it shows up fine in the GUI.  I think that /etc/adduser.conf may need adjusting as well, but so far it's fine.

Thanks for your help...

---

### Post by Habbit on 2008-06-09
Just out of curiosity, why do you need a particular account to have a particular UID?

---

