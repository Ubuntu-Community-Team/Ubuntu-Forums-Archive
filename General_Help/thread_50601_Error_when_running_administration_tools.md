---
title: "Error when running administration tools"
date: 2005-07-20
forum: General Help
---

### Post by javatron on 2005-07-20
im trying to add another user by clicking System > Administration > Users and Groups
but when i click users and groups, it asks me for my password. i type it in, and i get this error message:

Failed to run users-admin:
 Child terminated with 1 status

logging in and adding users was just working, then i tried to do it again and the error came up. can anyone help?

thanx & peace.

---

### Post by Xian on 2005-07-20
It's possible that you removed yourself from the admin group. 
If this is the case then boot into recovery mode and edit your /etc/sudoers file.

```
# User privilege specification
root	ALL=(ALL) ALL
username ALL=(ALL) ALL
```

---

