---
title: "how to create a user's home directory structure before their first login"
date: 2019-01-09
forum: General Help
---

### Post by bmullan2 on 2019-01-09
I know that** xdg-user-dirs-update **creates a User's Home directory structure (~/Desktop, ~/Documents, ~/Downloads etc) upon that User's first login.

But what if I wanted to have those all created *_**before**_* that user's 1st login ?   Is there a way to do this?


thanks in advance

brian

---

### Post by CatKiller on 2019-01-09
/etc/skel contains the skeleton of a new user's Home directory. When their Home directory is created, the contents of /etc/skel are copied to it.

---

### Post by bmullan2 on 2019-01-09
[solved]

I figured out how to do this.

logged in as root

**adduser testuser**

then

**su testuser -c xdg-user-dirs-update **

creates all the /home/testuser  subdirectories like ~/Documents, ~/Downloads etc.

---

### Post by TheFu on 2019-01-09
There is a skel/default setup that gets applied whenever a new userid is created.  It supports calling out to other programs/scripts, so anything you can automate, you can accomplish.  The manpage for useradd or adduser (I always get those mixed up) has more details. From the manpage:
```
       -k, --skel SKEL_DIR
           The skeleton directory, which contains files and directories to be
           copied in the user's home directory, when the home directory is
           created by useradd.

           This option is only valid if the -m (or --create-home) option is
           specified.

           If this option is not set, the skeleton directory is defined by the
           SKEL variable in /etc/default/useradd or, by default, /etc/skel.

           If possible, the ACLs and extended attributes are copied.
```
and
```
DESCRIPTION
       **adduser**  and  addgroup  add users and groups to the system according to
       command    line    options    and    configuration    information    in
       /etc/adduser.conf.   They  are  friendlier  front ends to the low level
       tools like useradd, groupadd and usermod programs, by default  choosing
       Debian  policy conformant UID and GID values, creating a home directory
       with skeletal configuration, running a custom script,  and  other  fea&#8208;
       tures.
...
       --home DIR
              Use  DIR  as  the user's home directory, rather than the default
              specified by the configuration file.  If the directory does  not
              exist, it is created and skeleton files are copied.
...
FILES
       /etc/adduser.conf
              Default configuration file for adduser and addgroup

SEE ALSO
       adduser.conf(5),   deluser(8),   useradd(8),  groupadd(8),  usermod(8),
       Debian Policy 9.2.2.
```
Hope that helps.

For example, if you use LDAP for user accounts, it is common to setup adding the userid to the LDAP DB and set the HOME directory to be on NFS storage.

BTW, if you solved this, please use the "thread tools" button near the top to mark it SOLVED. That helps the community not waste time.

---

