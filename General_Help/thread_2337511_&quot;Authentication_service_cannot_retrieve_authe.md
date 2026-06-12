---
title: "&quot;Authentication service cannot retrieve authentication info&quot;"
date: 2016-09-19
forum: General Help
---

### Post by riahc3 on 2016-09-19
Im having issues with a Ubuntu VM that I am trying to change the root password:

"Authentication service cannot retrieve authentication info"

Not sure why this message is popping up. How can I fix it?

---

### Post by ajgreeny on 2016-09-19
Have you already set a root password for your VM? 

Normally the root account is disabled in Ubuntu, so unless you have already enabled a root account, there is no password set for you to change.

See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for information on the way we normally make use of sudo to temporarily raise permissions to root.

---

