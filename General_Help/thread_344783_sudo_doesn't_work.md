---
title: "sudo doesn't work"
date: 2007-01-23
forum: General Help
---

### Post by Alex.Gorban on 2007-01-23
I'm always use sudo to do my administative tasks, but some time ago it stoped do anything. For instance, i'm typing 'sudo ls' <enter> and type my pasword afterwords, but that command do nothing wether folder I'm in. And such situation with all commands that i try to run with sudo. And now the only way to run commands as root is to swith user with command 'su'.

How I can fix my sudo? And how such situation occured?

---

### Post by taurus on 2007-01-23
What happens if you run this command from a terminal?

```
sudo aptitude update
```

---

### Post by Alex.Gorban on 2007-01-23
> **taurus said:**
> What happens if you run this command from a terminal?

```
sudo aptitude update
```

nothing at all.

But I've just found the solution.
When I've add myself into samba group 'Domain Admins' all my membership in other groups was cancled and in group 'admin' too. But according to the /etc/sudoers it is nessesary to be admin. Now I've just add myself to the group 'admin', relogin and sudo began to work.

Thank you all! :)

---

