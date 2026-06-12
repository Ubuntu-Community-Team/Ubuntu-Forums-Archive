---
title: "running shells at startup"
date: 2013-05-20
forum: General Help
---

### Post by 3wais on 2013-05-20
Hi,I was wondering how to make a shell run at startup. I do not use a GUI so I cannot just use startup applications. Is there a shell that runs by default when ubuntu boots up ?? If there is can I alter it or make it call other shells ??

---

### Post by oldos2er on 2013-05-20
Once you've booted and logged in, you're in bash. You can change shells with the *chsh* command.

---

### Post by redmk2 on 2013-05-20
> **3wais said:**
> Hi,I was wondering how to make a shell run at startup. I do not use a GUI so I cannot just use startup applications. Is there a shell that runs by default when ubuntu boots up ?? If there is can I alter it or make it call other shells ??

You don't need an interactive shell to run a script.  If you want to run a a script  (app) at start up.  You can use upstart or a line in /etc/rc.local to run the script in a non login shell at boot time.

What are you attempting to do?

---

