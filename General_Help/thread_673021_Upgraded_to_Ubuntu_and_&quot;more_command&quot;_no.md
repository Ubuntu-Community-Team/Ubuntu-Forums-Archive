---
title: "Upgraded to Ubuntu and &quot;more command&quot; not working"
date: 2008-01-20
forum: General Help
---

### Post by ocalld on 2008-01-20
Hi
Just upgraded Ubuntu 7.10 to 7.10, kernel 2.6.22-14-generic
Previous kernel was the one provided with the installation CD.

Before the upgrade, the "more command" worked.
Since the upgrade, the more command cannot even be found on my system.

Can somebody let me know what package "more" is part of???

It's a nightmare trying to work on terminal without more.

thanks
dan :confused::confused:

---

### Post by jimbren on 2008-01-20
Can you tell us exactly what you're typing into the console and what the result is?

---

### Post by ocalld on 2008-01-20
Hi

thanks for help, but i've manged to resolve the problem.
During the upgrade "util-linux" was removed, don't know why !!!

apt-get install util-linux and i now have more working agin.

Thanks for the reply.

Dan.

---

