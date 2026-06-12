---
title: "fsck error?"
date: 2008-02-02
forum: General Help
---

### Post by ElEdwards on 2008-02-02
I just booted up and saw the familiar checking of my hdd..... but this time, after the hdd check, I saw a message I hadn't seen before:

**fsck died with an exit code 1**

What is this?
...and should I be concerned?

Thanks :)
El

---

### Post by polmir on 2008-02-02
Type in terminal 
```
cat  /var/log/fsck/checkfs
```
or
```
cat /var/log/fsck/checkfs>info_fsck.txt
```
and please post out it

---

