---
title: "sudo authentication hangs terminal"
date: 2005-10-25
forum: General Help
---

### Post by Whatsisname on 2005-10-25
Greetings.

Since updating to 5.10 I have been experiencing a great deal of problems that I have been unable to resolve. One is that a few minutes after boot, sudo seems to hang as soon as I execute it, and not even ctrl+break or sending it a sigkill will make it snap out of it. Doesnt matter whether its within Xterm, ssh, or a tty terminal. Does anyone know what would cause that behavior, and how to fix it. I have a suspicioun that it only happens after I try starting X (having nvidia troubles), but haven't had time to fully test that hypothesis. I have had to set a root password and use "su root" to perform system administration in the meantime, although thats not really an ideal solution, i'd rather have sudo working properly, especially because root logins are prohibited for SSH.

Thanks for any help.

---

