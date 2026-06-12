---
title: "Change how ls work with wild cards?"
date: 2015-04-22
forum: General Help
---

### Post by chaaderf on 2015-04-22
Hello!

I'd like to change the way how ls is working when using wild cards in entry. Let me show an example:

Currently the way it is working is like this:
```
ls /etc/a*
/etc/adduser.conf  /etc/anacrontab

/etc/alternatives:
animate
animate.1.gz
awk
awk.1.gz
....
```

I.e. it shows all content that match the entry, but also content of directories that match. What I would like to see, is that only the directories are listed, not the content. Like

```
ls /etc/a*
/etc/adduser.conf  /etc/anacrontab  /etc/alternatives    ....
```

But the question is, how do I change this behavior? :confused:

---

### Post by Holger_Gehrke on 2015-04-22
The option '-d' or '--directory' should be helpful.

---

### Post by chaaderf on 2015-04-22
Thank you. ^^

---

