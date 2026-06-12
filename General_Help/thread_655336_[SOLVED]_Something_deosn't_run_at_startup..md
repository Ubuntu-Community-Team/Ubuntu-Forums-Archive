---
title: "[SOLVED] Something deosn't run at startup."
date: 2008-01-01
forum: General Help
---

### Post by dethredic on 2008-01-01
I have this command that needs to be run at startup.

```
sudo /usr/sbin/g15daemon
```

In terminal I went sudo visudo and added this line to the end of the file.

```
user ALL= NOPASSWD: ALL
```

I am assuming that line is supposed to make it so I don't need a password when I run the above command.

When I open up the sessions manager, and make a new session with this command:

```
sudo /usr/sbin/g15daemon
``` it does not work.

When I put that into a terminal, I still need to enter my password, and then it works.


So, what is wrong?

---

### Post by jken146 on 2008-01-01
[http://ubuntuforums.org/showthread.php?t=397916](http://ubuntuforums.org/showthread.php?t=397916)

---

### Post by santosh_gr on 2008-01-01
Change the section in sudoers file.  The nopasswd option should apply to root and %admin, not to user.

# User privilege specification
root ALL= NOPASSWD: ALL


# Members of the admin group may gain root privileges
%admin ALL= NOPASSWD: ALL

---

### Post by dethredic on 2008-01-01
Ok, I will find out if either of these workede tomorrow.

---

### Post by dethredic on 2008-01-01
great it works now!

Solved

---

