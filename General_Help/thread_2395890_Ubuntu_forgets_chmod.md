---
title: "Ubuntu forgets chmod?"
date: 2018-07-08
forum: General Help
---

### Post by teckthekid on 2018-07-08
Hello, 

I am using sshfs to mount a location which is also shared on local network.
It works great but every morning I have to to chmod to mount location or I can't access it from local network.

Any ideas on how to make it permanent?

Thanks.

---

### Post by QIII on 2018-07-08
Hello!

What is the exact command you are using for your sshfs mount?

How is the share on the remote machine set up?

---

### Post by teckthekid on 2018-07-08
I use  sshfs -o allow_other,reconnect,password_stdin login@111.222.333.444:/home/ home/user/ftp <<< "password"

---

### Post by QIII on 2018-07-10
It's not a good idea to use a password with ssh and a dangerous habit to get into even behind your router.

Anyway ... have you tried idmap=user?

---

