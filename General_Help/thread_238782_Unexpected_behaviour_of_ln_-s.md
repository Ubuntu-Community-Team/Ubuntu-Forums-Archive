---
title: "Unexpected behaviour of ln -s"
date: 2006-08-18
forum: General Help
---

### Post by jamadagni on 2006-08-18
Dear friends, please see the following Konsole session (opened by kdesu konsole):
```

root@chandas:/media# ln -s sda8 /suseh
root@chandas:/media# cd /suseh
bash: cd: /suseh: No such file or directory
root@chandas:/media# ls -l /suseh
lrwxrwxrwx   1 root root     4 2006-08-18 17:01 suseh -> sda8
```
I wonder why ln did not create the link to point to /media/sda8 but instead to just sda8.

---

### Post by givré on 2006-08-18
interesting, i made the same for my windows partition and it works fine.

---

### Post by tonym on 2006-08-18
I think this is because it is a symbolic link - the link contains exactly the characters you put in the ln command.  Try

ln -s /media/sda8 /suseh

---

