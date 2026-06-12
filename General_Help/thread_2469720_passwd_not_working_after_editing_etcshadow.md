---
title: "passwd not working after editing /etc/shadow"
date: 2021-12-07
forum: General Help
---

### Post by buntunoob2 on 2021-12-07
*solved* - I used sudo passwd which changes root, not the current user. As it does not output the username in this case I did not notice my error.

---

### Post by TheFu on 2021-12-07
To change the password for any user, use:
```
$ sudo passwd {username}
```

To change the current user's password, use:
```
$ passwd
```

Posts are typically not removed, so it isn't useful to ask for deletion.  What can be done, so not to waste people's time is to mark it as SOLVED using the thread tools button. Only the person who created the thread can do that. Help out the community, please.

---

