---
title: "Modify adduser to create /home/user/* directories automaticall"
date: 2006-11-08
forum: General Help
---

### Post by madtinkerer on 2006-11-08
Is there any way I can modify adduser.conf or run it with switches to have it automatically create directories in new users /home?  For example I want every newly created user to have /home/user/foo, /home/user/foo2, /home/user/foo3 automatically created in their /home/ directories.

---

### Post by blumi00GT on 2006-11-08
when you're using the console, you can use the command 'useradd' with the switch '-m'. Then the users home directory will be created and any contents under /etc/skel/* will be copied to the new users home.

See 'man useradd' for more information.

Blumi

---

### Post by mmcev106 on 2007-11-30
"adduser" is just a "friendly frontend" to "useradd".  You can set the default location of home directories created for new users using "adduser" in the "/etc/adduser.conf" file.

NOTE: If you're moving the home folder of current users on your system as well, you'll need to update the location for each user in "/etc/passwd".

---

### Post by mcduck on 2007-11-30
If you want to customize the way new user accounts are, just put those directories, all configuration and other stuff in /etc/skel directory. When new users are created all contents od /etc/skel are copied to the new user's home directory.

---

### Post by geirha on 2007-11-30
Read adduser.conf's manpage. ```
man adduser.conf
```

You probably want to change DHOME. GROUPHOMES might be something you want to look at as well.

---

