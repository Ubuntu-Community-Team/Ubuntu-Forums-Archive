---
title: "[SOLVED] is there a command for this?"
date: 2007-09-27
forum: General Help
---

### Post by iamBevan on 2007-09-27
Just wondering if there is a terminal command to tell you how much space you have used/have left on your HDD? I've looked, but haven't had any luck :(

Cheers in advance

.Kev.

---

### Post by jimrz on 2007-09-27
> **iamBevan said:**
> Just wondering if there is a terminal command to tell you how much space you have used/have left on your HDD? I've looked, but haven't had any luck :(

Cheers in advance

.Kev.
```
df
```

 Display free disk space

---

### Post by akiratheoni on 2007-09-27
df will give you disk space, but if you use:

```
df -h
``` 

It will change blocks into MB and GB.

---

### Post by olejorgen on 2007-09-27
Remember to mark thread as solved (thread tools -> mark as solved)

Also, it's generally a good idea to include the core idea of your question in the post title. eg. Command for showing free space?

---

