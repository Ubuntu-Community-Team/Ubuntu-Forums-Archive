---
title: "Show all uses and their permissions?"
date: 2007-10-10
forum: General Help
---

### Post by armeck on 2007-10-10
I was wondering if there was a command line way to list all the users of a system and their respective privileges?  Similar to 'ls -l' for files.  It needs to be a command line option only...

---

### Post by nick_h on 2007-10-10
For a list of users type:
```
cat /etc/passwd
```
and for a list of groups with the users that belong to each, type:
```
cat /etc/group
```

---

### Post by thirddeep on 2007-10-10
For access rights, you can use :
```
sudo find -user USERNAME /LOCATION
```

Thd.

---

### Post by armeck on 2007-10-10
Thanks guys that did it!

---

