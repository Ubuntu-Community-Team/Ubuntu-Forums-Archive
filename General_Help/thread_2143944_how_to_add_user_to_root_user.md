---
title: "how to add user to root user"
date: 2013-05-10
forum: General Help
---

### Post by nrmurali on 2013-05-10
hi,

please let me know how to add a user to root user so that every thing done by root should have to be done by this user.

thanks in advance

---

### Post by prodigy_ on 2013-05-10
[https://help.ubuntu.com/community/RootSudo#Allowing_other_users_to_run_sudo](https://help.ubuntu.com/community/RootSudo#Allowing_other_users_to_run_sudo)

---

### Post by varunendra on 2013-05-11
> **nrmurali said:**
> please let me know how to add a user to root user so that every thing done by root should have to be done by this user.

The first user created on the machine already can do everything (with sudo, or gksu, or sudo su) that a user may ever need to do as root. If a task really needs you to be root, you can temporarily become "root" with "**sudo su**" command. Follow the link provided by prodigy to see further details on this. I'm posting here some common use examples -

[COLOR="#800000"][SIZE=3]**_Adding an Existing User to an Existing Group_ :**[/SIZE][/COLOR]
To grant users the ability to do things as root, simply add them to "sudo" group. For example, to add a user "newuser" to this group -
```
sudo adduser newuser sudo
```
*(the first 'sudo' is there to grant you the root permission, as this task needs that. The command part is [COLOR="#800000"]adduser newuser sudo[/COLOR])*

To grant this user all the same privileges as the first user, check all the groups that the first user is a member of, then make the new user member of all those groups just like above. For example, if the first user (created while installation) is "firstuser", then,

To see all the groups that "firstuser" is member of -
```
groups firstuser
```

Output will be something like -
> **firstuser :** firstuser adm disk cdrom sudo dip plugdev lpadmin sambashare vboxusers
..means user "firstuser" is a member of a total of 10 groups - "[COLOR="#000080"]firstuser, adm, disk,........., vboxusers[/COLOR]".

Now, to grant "newuser" the membership of "adm" group -
```
sudo adduser newuser adm
```

[COLOR="#800000"][SIZE=3]**_Removing a user from a group_ :**[/SIZE][/COLOR]
Let's say you added the user "newuser" to "adm" group by mistake, or for some other reason you want to remove him from that group. Simply do -
```
sudo deluser newuser adm
```
..this ^^ will remove the user "newuser" from the "adm" group.

For more info on manipulating users & groups, see the manpages of these commads using -
[B]man adduser
man deluser[/B]
..commands.

Now something you should know and ALWAYS keep in mind: The "root" is disabled by default in Ubuntu for a good reason. Enabling and logging in as root or working with root privileges All the Time is almost never required. If you do so without a good reason and without understanding the possible consequences (of a wrong action), you may be shooting yourself in the foot, or maybe in the head!! That being said, some more info -

The "root" is a member of its own group - "root". As such, adding a user to this group *should* grant them the same powers as root, but I can't say for sure because I never tried that (if you are experimenting on the current user, you may have to log-out -> login again for the change to take effect). Despite that being fairly easy to do, just like the above examples, it is recommended to NOT DO SO. Almost everything you may ever need to do as root can be done with sudo, so use that group instead.

Hope it answers your question as well as serves as a general advice to anyone interested. :)

---

### Post by lisati on 2013-05-11
To add to what varunendra was saying, some of the background to using **sudo** with Ubuntu is described here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

