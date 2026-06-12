---
title: "sudo command - strange behavior"
date: 2008-01-03
forum: General Help
---

### Post by atomas on 2008-01-03
hi
I am using ubuntu gutsy and whenever I use sudo + command in a consol I do not have to enter the password to have root access for subsecant command. meaning that anyone using the computer after me could have root access. is this the normal behavior? what should I do to exit sudo(root access)? I tought that sudo was good for only one command at  a time.

thanks for replies

---

### Post by sciencewhiz on 2008-01-03
By default it will not prompt for a password for 15 minutes. You can change it in the sudoers file, however. Read the sudo and sudoers man page for more details.

---

### Post by SOULRiDER on 2008-01-03
Yes, its good for one command at a time. When you use sudo though, it will not ask for your password again for some time (around 15 minutes). After that time is up it will once again ask for the passowrd.

---

### Post by RC Howe on 2008-01-03
The sudo command remembers your password for 15 minutes after you last entered it, so if you are executing a lot of things as root you do not have to type your password every time. Only commands beginning with sudo are root-level, so if I run a command right after I've run a sudo command the normal command is run as you (not root).

Long story short, it's completely normal. If you are concerned about someone else coming in and executing a command, type sudo -K to clear the 15 minute timestamp. You will not be required to enter a password for sudo -K.

---

