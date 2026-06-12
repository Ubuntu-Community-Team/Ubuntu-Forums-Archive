---
title: "How do i find the ubuntu version from a script (Solved)"
date: 2006-10-19
forum: General Help
---

### Post by kkass on 2006-10-19
I have a shell script that needs to do some things differently based on what version of Ubuntu it is run on.  What is the best way for me to find out this information?

The only semi-reliable way I can think of now is to grep the sources.list, file.  But I am not sure I want to trust this.

(It is important for me to know if I am running breezy, dapper, etc.. It does not matter if I am running Ubuntu, Kubuntu, etc..)

Any suggestions?

---

### Post by raul_ on 2006-10-19
```

lsb_release -a

```

There is also a file that contains that information but i don't remember which one...when i find it i'll post it

EDIT: the file is /etc/issue

---

### Post by kkass on 2006-10-19
Thanks!  That will be a big help.

---

### Post by chalex on 2006-10-19
or /etc/lsb-release

---

