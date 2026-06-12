---
title: "Newly created users belong to &quot;users&quot; group, although /etc/adduser.conf disagrees"
date: 2022-12-20
forum: General Help
---

### Post by ne29914 on 2022-12-20
When creating new users on my system, they all have group "users", GID=100, although my /etc/adduser.conf says something else.
The pertinent lines are:
```
# The USERGROUPS variable can be either "yes" or "no".  If "yes" each
# created user will be given their own group to use as a default.  If
# "no", each created user will be placed in the group whose gid is
# USERS_GID (see below).
USERGROUPS=yes


# If USERGROUPS is "no", then USERS_GID should be the GID of the group
# `users' (or the equivalent group) on your system.
USERS_GID=100

```
Is there another configuration flie somewhere that I've overlooked?
Or is something else wrong?

TIA.

---

