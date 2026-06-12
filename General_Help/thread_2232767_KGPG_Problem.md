---
title: "KGPG Problem"
date: 2014-07-04
forum: General Help
---

### Post by redbikemaster on 2014-07-04
So, I've been using Kgpg successfully until recently. Now, when I try to open Kgpg, I get this:

```

gpg: can't open `/home/redbikemaster/.gnupg/pubring.gpg'
gpg: keydb_search_first failed: file open error
tru::1:1397101464:0:3:1:5

```

I really need these keys ASAP, so any and all help would be greatly appreciated. Thanks.

---

### Post by bapoumba on 2014-07-06
Does your user own /home/redbikemaster/.gnupg/pubring.gpg ?

---

### Post by redbikemaster on 2014-07-06
It be owned by root. Bad?

---

### Post by bapoumba on 2014-07-06
Well, either you run it as root or if you want it to be run by your user, you should own it :)
What was your previous setup ? Run as root or run as user ?

---

### Post by redbikemaster on 2014-07-06
[ATTACH=CONFIG]254510[/ATTACH]

...I have never had to enter admin password, so I'm assuming it was originally run as user. Does that sound right? It's just the app KGpg.

---

### Post by bapoumba on 2014-07-06
As I'm not using it, I do to know if running as user sounds right or not. Been browsing gnupg and kgpg docs and it is not obvious if it should be run as user or root. From ancient times when I used to use seahorse, I did not use a password either.

In any case :
```
sudo chown redbikemaster:redbikemaster ~/.gnupg/pubring.gpg
```
Will make the file belong to your user and user group, I guess you do not want others to be able to access it.

Who owns the ~/.gnupg/ file btw ? A change in ownsership is always curious and should not happen by luck (or bad luck ;)).

Edit : on my setup, my user owns the whole file :
```
bapoumba@SonyBlue:~$ ls -la .gnupg/
total 24
drwx------  2 bapoumba bapoumba 4096 juil.  5 20:15 .
drwxr-xr-x 37 bapoumba bapoumba 4096 juil.  6 12:13 ..
-rw-------  1 bapoumba bapoumba 9398 mai   25 11:48 gpg.conf
-rw-------  1 bapoumba bapoumba    0 mai   25 11:48 pubring.gpg
-rw-------  1 bapoumba bapoumba 1200 mai   30 12:23 trustdb.gpg

```

---

### Post by redbikemaster on 2014-07-06
Will do here in a sec. Funny, everything else is owned by me (redbikemaster). Weird.

---

### Post by redbikemaster on 2014-07-06
Well, you're a hero. Thanks. That was it. I can't believe I didn't think to check that.

Have an Ubuntu bean!

Or, a trophy from the last place trophy thread:
[ATTACH=CONFIG]254511[/ATTACH]

---

### Post by bapoumba on 2014-07-06
:lol:
Thanks for marking your thread as solved !

---

