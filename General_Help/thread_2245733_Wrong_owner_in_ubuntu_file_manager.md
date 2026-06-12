---
title: "Wrong owner in ubuntu file manager"
date: 2014-09-25
forum: General Help
---

### Post by orloff34 on 2014-09-25
Hi,

I am using Ubuntu 14.04.01 (64 bit) ans I encountered following problem:

Using the properties pop up (right mouse klick) from the file manager for any of the system files or folders my user name is displayed as the owner,  group is root.

When checking the same folders and files in the terminal with ls -l owner and group is root:root as it should be. What is working wrong?

Best regards
orloff34

---

### Post by orloff34 on 2014-09-26
So I found the failure myself. For some reason, I don't know the file etc/passwd was corrupted :confused:: 
The first entry in this file for root was
```
root:x:0:0:**thomasb**,,,:/root:/bin/bash

instead of

root:x:0:0:**root**,,,:/root:/bin/bash
```
After correction of the passwd file everything is working fine.

orloff34

---

