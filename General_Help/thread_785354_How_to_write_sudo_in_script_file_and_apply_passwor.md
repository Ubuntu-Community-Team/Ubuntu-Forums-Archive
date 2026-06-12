---
title: "How to write sudo in script file and apply password?"
date: 2008-05-07
forum: General Help
---

### Post by abcuser on 2008-05-07
Hi,
I need to execute one statement that only user1 has permitions to do. But this user does not have a read/write privileg to file.

So now I have two scripts:
==========================
1. script executed by root
==========================
cd /directory
chmod 777 *

===========================
2. script executed by user1
===========================
some commands that access files in /directory


Is there any way I could write only one script. I would need something like: sudo and apply my password in file to execute first script file. How to write sudo and apply password?
Thanks,
Abcuser

---

