---
title: "CD Writer automatic permission"
date: 2007-02-13
forum: General Help
---

### Post by emlee5 on 2007-02-13
Hi all,

I would like to allow all users to burn CDs without having to type in:

sudo chmod 777 /dev/sg0 sg1 sg2 etc

at the terminal.

I am using Dapper and would like to know if there is a script where I can have this run automatically after login.

Any help appreciated

Evan

---

### Post by frafu on 2007-02-14
Hello,

I have moved this thread to the General Help Forum where it has a better chance to get answers.

Have a nice day.

Francesco
Edit/Delete Message

---

### Post by emlee5 on 2007-02-16
Hi again

thanks for moving this thread - unfortunately still no reply..

there must be a way of running terminal commands during log in?

Evan

---

### Post by n00bish on 2007-02-16
I believe you can just add the user to the "cdrom" group - run the following command to add them:

```

sudo adduser `whoami` cdrom

```

That will add yourself - replace `whoami` with their username to add them to the group.

---

