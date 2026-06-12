---
title: "CLI /dev/fd01722"
date: 2005-07-28
forum: General Help
---

### Post by Sweezel on 2005-07-28
To format a floppy with fdformat /dev/fd0u1722, I had to delete the existing /dev/fd0u1722 as root and recreate it using mknod /dev/fd0u1722 b 2 60.

Why did I have to do this?


TIA

---

### Post by amohanty on 2005-07-29
Why were you not able to use:
>> fdformat /dev/fd0


AM

---

