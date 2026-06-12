---
title: "'locate' command is broken in 6.10"
date: 2007-01-23
forum: General Help
---

### Post by joemo75 on 2007-01-23
The 'locate' command is broken in Ubuntu 6.10...

Example:
```
user@machine:~$ locate *.gif
locate: fatal error: search_db: open: '/var/lib/slocate/slocate.db': Permission denied
```

---

### Post by llamakc on 2007-01-23
It works fine for me as a user. Have you recently installed? I'd update with:

sudo updatedb

and try again.

---

### Post by lamego on 2007-01-23
That message means the locate db was not created yet.
You will need to create it with the already suggested updatedb command.

---

### Post by Ramses de Norre on 2007-01-23
locate is very fast because it uses a database file and doesn't look through the real filesystem. This has disadvantages too though: the database represents your filesystem like it was the last time updatedb ran (which is in a cron job that runs daily).
So you need to create the database the very first time (by the already mentioned sudo updatedb) and when you want the use locate to find newly created files you'll need to update the db again (except if cron was faster).

---

### Post by joemo75 on 2007-01-24
> **llamakc said:**
> It works fine for me as a user. Have you recently installed? I'd update with:

sudo updatedb

and try again.

No, the database is there, however it has the wrong permissions, just like the error says.  Can I just make it world readable and be done with it?

---

### Post by llamakc on 2007-01-24
```

root@llamakc:/var/lib/slocate# ls -lh
total 2.3M
-rw-r----- 1 root slocate 2.3M 2007-01-24 07:35 slocate.db

```

...are the correct permissions. Have you or have you not ran:

```

sudo updatedb

```

Yet?

That must be done, either by you manually or when cron runs it. This is why I asked if you had a recent install.

---

### Post by joemo75 on 2007-02-22
This bug was fixed with an slocate patch today.  Thanks everyone for your help.

---

### Post by majeru on 2007-05-25
I don't see it as a bug but as a feature. I think the users who should be able to search through all the files available in the system should belong to the slocate group, and overriding the default permissions of the database file is a security issue.

---

### Post by fragos on 2007-05-25
It would appear that you weren't a member of the slocate group.

---

