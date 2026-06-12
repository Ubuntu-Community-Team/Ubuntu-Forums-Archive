---
title: "What does # mean in command lines?"
date: 2017-05-13
forum: General Help
---

### Post by limiv on 2017-05-13
For example: 
[FONT=arial]**# find /home -iname random.txt**[/FONT]

---

### Post by QIII on 2017-05-13
Assuming a default installation of a Debian-based distro, that means that you are working with elevated privileges, "as root" or are logged in as root.  The last is not recommended.

Are you following instructions you found on the web?

---

### Post by &amp;KyT$0P# on 2017-05-13
It either means it's a comment (not a command to run), or it means you should run that command as root.  In this case, some context is needed to figure out which it is.

---

### Post by deadflowr on 2017-05-13
Depends.
If running from a script it means omit this line and do not read it.
But if running as root user it indicates that you are running as the root user
normal user is something like
```
bob@thecarwash:~$
```
and root would be
```
root@thecarwash:~#
```

sometimes bloggers posting how-to's will simply put the # down as an indication that you are to run as root when running the commands they post in the how-to.
(and of course never explain that's what that is)

---

### Post by Habitual on 2017-05-13
n/m. halogen2 nailed it.
root prompt or c-line comment.

---

