---
title: "Autostart Keep-Daemon"
date: 2007-02-15
forum: General Help
---

### Post by AllesMeins on 2007-02-15
I want to use "Keep" to manage some of my backups. It seems to work fine with one exception. After every restart i've to start Keep and start the "backup daemon" manually. How can i let it load automatically at startup?

---

### Post by dcstar on 2007-02-15
> **AllesMeins said:**
> I want to use "Keep" to manage some of my backups. It seems to work fine with one exception. After every restart i've to start Keep and start the "backup daemon" manually. How can i let it load automatically at startup?

System-Preferences-Sessions-Startup Programs (in Gnome), or:

Put it in a startup script in /etc/init.d, and then create the appropriate link to the /etc/rc2.d directory.

You can get detailed instructions by doing a forum search.

---

### Post by AllesMeins on 2007-02-16
Thanks for the answer. I think i know now how i could start it at startup. But there is a new problem: i've no idea what to start. It seems there is no new process created when starting the daemon. When it is running i can't find any process-name which would indicate that this was started by keep.

---

