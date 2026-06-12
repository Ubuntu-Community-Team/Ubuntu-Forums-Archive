---
title: "Have I set up my second user correctly"
date: 2017-05-11
forum: General Help
---

### Post by Robbyx on 2017-05-11
I have two users on my grome 16.04.2:


Primary user:
Robin
Home directory: /home/test
Main group robin
ID 1001


Additiional Admin user:
test2
Home: /home/test2
Main group: test2

These are my main groups. Have I set up the memberships sensibly.

adm: members: robin and test2
robin: members: robin and test2
test: robin
test2: no members ticked
users: no members ticked

---

### Post by deadflowr on 2017-05-11
is adm shorthand by you or the group it's in?
If it's the adm group then that related to the ability to read log files and is not an admin account group.
The admin account group is sudo on Ubuntu; other distros use groups like wheel and admin for the admin group.

---

### Post by Robbyx on 2017-05-11
the group's name is adm. I note your comments.

I assume you concluded that my membership attachments to the groups, as outlined, should not cause problems.

---

### Post by deadflowr on 2017-05-11
I made no conclusions .
Just stating that the adm group is not an admin group.
And was wondering if that was the groups name or if it was you were just shortening admin to adm.

per this part:
```
adm: members: robin and test2
robin: members: robin and test2
test: robin
test2: no members ticked
users: no members ticked
```
I see no real problems.
Wonder who test and users are, though.
I guess this is what you get from the /etc/group file?

---

### Post by steeldriver on 2017-05-11
Group `test2` would be the default user private group for user `test2`

Group `users` is an oldschool group that's present by default since before the days of user private groups

```

$ getent group users
users:x:100:

```

---

### Post by Robbyx on 2017-05-11
> **steeldriver said:**
> Group `test2` would be the default user private group for user `test2`

Group `users` is an oldschool group that's present by default since before the days of user private groups

```

$ getent group users
users:x:100:

```


yes, and test is the group for robin. 

I had a crash and could not get back into the original users but was able to create a new user with admin powers, but I called it test and have not been able to change it to something more sensible for an in use main user.

---

