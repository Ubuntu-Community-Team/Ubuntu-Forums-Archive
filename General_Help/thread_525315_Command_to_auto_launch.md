---
title: "Command to auto launch?"
date: 2007-08-14
forum: General Help
---

### Post by jusmurph on 2007-08-14
Is there a command, rather than GUI (for a script) for launching programs when Ubuntu loads?

Is there also a way to pause terminal scripts?

---

### Post by john8791 on 2007-08-16
Not sure I fully understand your question.  I don't know a command, but what's wrong with **System->Preferences->Sessions->Startup Programs**?  Otherwise, setting up something global like in /etc/init.d/rc.local would do it but this will presumably load before the X-server is started.

---

### Post by jusmurph on 2007-08-16
> **john8791 said:**
> Not sure I fully understand your question.  I don't know a command, but what's wrong with **System->Preferences->Sessions->Startup Programs**?  Otherwise, setting up something global like in /etc/init.d/rc.local would do it but this will presumably load before the X-server is started.

Thanks for that mate. Not what i was after, i assume feature is just not there.

---

