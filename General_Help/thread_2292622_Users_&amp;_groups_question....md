---
title: "Users &amp; groups question..."
date: 2015-08-29
forum: General Help
---

### Post by james139 on 2015-08-29
When you create a new user on a system, which groups on the system are they automatically assigned to?

---

### Post by Dennis N on 2015-08-29
None, except the user's own group. That is, if the new username is fred he's only in the group fred.

---

### Post by james139 on 2015-08-29
OK, thanks, that's what I thought. I was struggling to set file permissions for a folder and found that two other users I'd created were in my own user group so they were getting the same permissions set. I can't figure out how I did this (if I did anything). Weird.

---

### Post by Dennis N on 2015-08-29
You probably already know this, but in case not, you can find out the groups a user is in from the command: **groups username**.

```
dmn@Daphne:~$ groups dmn
dmn : dmn adm cdrom sudo dip plugdev lpadmin sambashare

```

---

### Post by steeldriver on 2015-08-29
It depends *how* you create the user I think: **useradd** doesn't add any additional group membership, but **adduser** defaults to the groups mentioned in /etc/adduser.conf i.e.

```

# Set this if you want the --add_extra_groups option to adduser to add
# new users to other groups.
# This is the list of groups that new non-system users will be added to
# Default:
#EXTRA_GROUPS="dialout cdrom floppy audio video plugdev users"

# If ADD_EXTRA_GROUPS is set to something non-zero, the EXTRA_GROUPS
# option above will be default behavior for adding new, non-system users
#ADD_EXTRA_GROUPS=1

```

---

