---
title: "Can't reset password with 'set password by hand'"
date: 2006-11-29
forum: General Help
---

### Post by leeportnoff on 2006-11-29
I created several user accounts with 
System > Administration > Users and Groups

I created a default password using 'set password by hand'
One user has changed her password and forgotten it.

I tried going back to 'set password by hand' and putting in a new value.  But the password is still invalid.

---

### Post by doobit on 2006-11-29
If you are root, all you need is to use the ```
passwd <username> 
``` command in the /home directory in a terminal. If the user forgot the username, it's easy to figure out because the user's folders in /home have the same names as the usernames.
```
ls 
```

---

### Post by lordchaos on 2006-11-29
sudo passwd <username>

---

### Post by doobit on 2006-11-29
If you are root you don't need sudo. Actually, I'm not sure sudo is enough to allow you to change the password of another user. I'll have to try it.

---

### Post by Ramses de Norre on 2006-11-29
Sudo can do it;)

---

