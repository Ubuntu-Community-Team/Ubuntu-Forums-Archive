---
title: "Unable to log in"
date: 2013-04-08
forum: General Help
---

### Post by mayagrafix on 2013-04-08
I created a new user account but when I try to log on I get sent back to the log in screen. No error notice, no wrong password notice, just back to beginning log in screen as if nothing happened. The other user account works perfectly.

Any ideas on how to fix?

Thanks for any help.

---

### Post by PowerBarry43 on 2013-04-08
if you open a terminal from your working user can you use 

```
su - <new username>
```

if you can successfully log in that means there's nothing wrong with the user otherwise you may want to remove the user and re-add it with:

```
userdel <new username>
adduser <new username>
```

---

### Post by mayagrafix on 2013-04-09
Great! that worked.

---

