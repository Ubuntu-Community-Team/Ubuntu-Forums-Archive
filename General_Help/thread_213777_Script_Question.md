---
title: "Script Question"
date: 2006-07-11
forum: General Help
---

### Post by cssutto on 2006-07-11
How do you enter a password in a script that requires a password to execute?

CSSJR

---

### Post by mogelhead on 2006-07-12
Is it some linux command that you are going to execute from your script? In that case: which command?

Which scripting language are you talking about, bash?

---

### Post by Ramses de Norre on 2006-07-12
We need more info.. Maybe you could post the part of the sript you're having trouble with or explain it a bit more (and tell us which language you use).

---

### Post by cssutto on 2006-07-12
Thanks.

But I have changed my mind.

I am going at it a different way.

CSSJR

---

### Post by 3rdalbum on 2006-07-12
> **cssutto said:**
> Thanks.

But I have changed my mind.

I am going at it a different way.

CSSJR

...just as long as that different way is by executing the script as root user, e.g:

```

chris@compaq:~$ sudo su
Password: 
root@compaq:/home/chris# ./scriptname.sh

```

---

