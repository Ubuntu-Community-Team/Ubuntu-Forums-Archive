---
title: "How to change Stack Size limits?"
date: 2013-05-20
forum: General Help
---

### Post by Nordico on 2013-05-20
Tried with ulimit, but the command "ulimit -s unlimited" returns:

bash: ulimit: stack size: cannot modify limit: Operation not permitted

I can use "ulimit -s N" if N is lower than the current limit, but I can't raise it. From doing some research about this, I found that apparently this is how ulimit behaves, but couldn't find how to increase it in another way. The pages I found are of specific work groups and seem to be like "admin to user" directions (only suitable for threir environment).

(I am using Xubuntu 11.10)

---

