---
title: "apt-cache very slow only as root."
date: 2014-02-16
forum: General Help
---

### Post by telefrancisco on 2014-02-16
Hello.

When using apt-cache to search for some package (in the usual way, e.g.: apt-cache search firefox ) it can take a lot of time (more than 10 minutes) when doing so as a root user.
Funny thing is that doing the same thing as a plain user, it gives the output in seconds...

What can I do for apt-cache to work well as root too?

Thanks.

---

### Post by coldcritter64 on 2014-02-16
> **telefrancisco said:**
> Hello.

When using apt-cache to search for some package (in the usual way, e.g.: apt-cache search firefox ) it can take a lot of time (more than 10 minutes) when doing so as a root user.
Funny thing is that doing the same thing as a plain user, it gives the output in seconds...

What can I do for apt-cache to work well as root too?

Thanks.How are you "getting root user", is it in terminal (with sudo -i for example) or is this a graphical root login question ?

---

### Post by epikvision on 2014-02-16
Perhaps, you should restart your computer and try again.

Instead of running the commands as a root user (it can get dangerous), why don't you use something like:

```
 $ sudo apt-cache search <application> 
```

---

### Post by vasa1 on 2014-02-16
What difference do you expect by running apt-cache as root?

---

### Post by deadflowr on 2014-02-16
> What can I do for apt-cache to work well as root too?

What do you think is the added benefit of running it as root?
(Hint: There is an answer, and it is none)

You're not installing,removing,updating, or manipulating anything.
Only viewing.

---

### Post by lisati on 2014-02-16
Running as root? Why?

Please see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by telefrancisco on 2014-02-17
Solved.

Deleting some old library got my problem solved and it worked in root as fast as regular user.

Thanks for all the answers.

---

