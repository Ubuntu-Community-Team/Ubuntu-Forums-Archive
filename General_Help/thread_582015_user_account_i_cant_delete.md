---
title: "user account i cant delete"
date: 2007-10-19
forum: General Help
---

### Post by Foresthello on 2007-10-19
ok there is a user account that is named fidonet at the loggin screen and when i try to find the account in user settings it doesent show it, it showed the following users

forest
root
sashroot

but it dident show the fidonet account what should i do.

thanks for the help in advance

---

### Post by mlissner on 2007-10-19
I'm not sure exactly what you mean by "in the user settings", but try this: ```
sudo deluser fidonet
```
Good luck.

---

### Post by Foresthello on 2007-10-20
well that diddent work it says there is no such user but there is

---

### Post by mlissner on 2007-10-20
Interesting. Try making such a user, and then deleting them. To make them, do ```
sudo adduser fidonet
```

To delete them, do the code from the other post. That might do the trick if the user was improperly deleted the first time, but I'm just taking a shot at it. Others might have a better idea.

---

