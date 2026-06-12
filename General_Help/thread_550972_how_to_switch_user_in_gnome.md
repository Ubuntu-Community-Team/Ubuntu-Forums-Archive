---
title: "how to switch user in gnome"
date: 2007-09-14
forum: General Help
---

### Post by bullish on 2007-09-14
I login to gnome with my local account, but sometimes I need to access some files on an NFS share that require me to use an NIS account. This is fine to do at the command line, but is it possible to do it in gnome GUI also? I wonder if I can stay logged in with my current 'local' session, and su into my NIS account to access the files in GUI file manager.

Thanks,

---

### Post by tszanon on 2007-09-14
> **bullish said:**
> I login to gnome with my local account, but sometimes I need to access some files on an NFS share that require me to use an NIS account. This is fine to do at the command line, but is it possible to do it in gnome GUI also? I wonder if I can stay logged in with my current 'local' session, and su into my NIS account to access the files in GUI file manager.

Thanks,
Press the Shut down button and choose "Switch user" in the dialog box. The labels may change a little depending on the Ubuntu version you're using, but it's something similar to this.
Your current session will remain open, password protected, and a new gnome-session will be run. You can switch between them using Alt+F7 (first session) and Alt+F8 (second session).

When you log out from the second session, you will automatically go back to the first session.

---

