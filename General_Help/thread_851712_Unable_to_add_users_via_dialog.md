---
title: "Unable to add users via dialog"
date: 2008-07-06
forum: General Help
---

### Post by cpe111 on 2008-07-06
Trying to add a user via the System/Administration/Users and Groups dialog but I am not being prompted for a password and the Add User button is greyed out.

I get the same if I try sudo users-admin    and also if i try    sudo -i; users-admin.

Any ideas? 

Thanks

---

### Post by Rocket2DMn on 2008-07-06
Did you click the Unlock button at the bottom?  Then you can select your username (it defaults to this) and type in your password.

---

### Post by iaculallad on 2008-07-06
What about adding a user through the terminal: Command below creates a user that belongs to "admin" group.

```
sudo useradd -c "FirstName LastName" -g admin -d /home/username -s /bin/bash username
```

---

### Post by cpe111 on 2008-07-06
That worked fine - thanks. For some reason I assumed 'unlock' would reset the failed password count to unlock a locked id :)

---

