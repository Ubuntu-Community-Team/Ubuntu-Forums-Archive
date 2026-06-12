---
title: "in User Settings, groups are repeated"
date: 2008-06-29
forum: General Help
---

### Post by CodeNosher on 2008-06-29
I'm on 7.10 and found in Users and Groups the group is repeated.

To see this try this:
System|Administration|Users and Groups click on Manage Groups.

It lists the groups, but it lists the groups multiple times.  Is there a way to prevent this?

---

### Post by mempman on 2008-06-29
print the output of:

```

cat /etc/group

```

---

