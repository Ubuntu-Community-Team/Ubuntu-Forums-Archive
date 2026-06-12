---
title: "User Groups"
date: 2007-02-07
forum: General Help
---

### Post by CarlosinFL on 2007-02-07
I don't understand something about "groups" on my Ubuntu laptop. My username is "carlos" and I created a group called "itgeeks" and I see it listed in **/etc/gshadow** as follows:

```
itgeeks:!::carlos

```

As you can see my user seems to be a member of "itgeeks" but when I run the "groups" command in CLI, I don't see myself as a member of that group. Why?

```
carlos : carlos adm dialout fax cdrom floppy tape audio dip video plugdev lpadmin scanner admin
```

When I use the graphical tool, I see the following:

[IMG]http://img525.imageshack.us/img525/1641/groupsdh3.png[/IMG]

---

### Post by kpatz on 2007-02-07
You need to add yourself as a member of the group in /etc/groups as well.  The easiest way is to use **sudo adduser carlos itgeeks**.

---

### Post by CarlosinFL on 2007-02-07
So when I run the suggested above, it will ignore the adduser command since "carlos" already exist and then just add me to the group. Just as if I were to issue the usermod command...?

---

### Post by feverish on 2007-02-26
man adduser says:
>  Add an existing user to an existing group
       If called with two non-option arguments, adduser will add  an  existing
       user to an existing group.


---

