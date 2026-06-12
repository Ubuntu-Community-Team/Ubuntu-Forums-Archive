---
title: "How do i add a /home direcory to the user?"
date: 2008-05-08
forum: General Help
---

### Post by descentspb on 2008-05-08
I need to create the /home directory for a user, who doesn't have any. And i am in ubuntu-server, so i can use only command-line interface. Thanks for your help!

---

### Post by Monicker on 2008-05-08
Is there no home directory specified in /etc/passwd for them?
```

johndoe:x:1000:1000:John,,,:/home/johndoe:/bin/bash
```

You can edit /etc/passwd and specifiy it, then "mkdir /home/username", "chown username.username /home/username".

---

### Post by latna on 2008-05-08
You should create users with the adduser command. It automatically creates the home directory. But since you already have a user created:
```
usermod --home HOME_DIR
```
Of course replace HOME_DIR with the name of the directory.

---

### Post by descentspb on 2008-05-08
Thanks, guys, it works now

---

### Post by Monicker on 2008-05-08
> **latna said:**
> You should create users with the adduser command. It automatically creates the home directory. But since you already have a user created:
```
usermod --home HOME_DIR
```
Of course replace HOME_DIR with the name of the directory.

usermod completely slipped my mind.  That would be the preferred way of doing it.

---

