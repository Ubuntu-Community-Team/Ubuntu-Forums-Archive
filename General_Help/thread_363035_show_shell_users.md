---
title: "show shell users"
date: 2007-02-16
forum: General Help
---

### Post by blanks on 2007-02-16
Anyone know how to list the usernames associated with all open shells?  I tried the who command and it doesn't do what I want.

For example, login as user "blanks"
$> who
    blanks ...
$> su - root
$> who
     blanks ...
$> su - anotherUser
$> who
     blanks...

I'm looking for a command that would show all 3 users with running shells...
Thanks!

---

### Post by llamakc on 2007-02-16
ps aux |grep [b]ash | grep pts

Or in the console (sans X)

ps aux |grep [b]ash | grep tty | grep -v startx

---

### Post by blanks on 2007-02-16
Wunderbar!

Thanks

---

### Post by Ramses de Norre on 2007-02-16
```
finger
```

---

### Post by llamakc on 2007-02-16
> **Ramses de Norre said:**
> ```
finger
```

Heck! I haven't used that in so long I forgot about it. Thanks.

---

### Post by blanks on 2007-02-16
Yeah, I tried finger.  I get the same result as who.

---

### Post by jeffathehutt on 2007-02-16
Don't forget w :) 

```
w
```

---

