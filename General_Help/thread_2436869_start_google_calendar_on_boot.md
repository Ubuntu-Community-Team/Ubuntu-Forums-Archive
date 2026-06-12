---
title: "start google calendar on boot"
date: 2020-02-14
forum: General Help
---

### Post by jgw on 2020-02-14
I want to start google calendar on boot.  As far as I can tell it is synced with the gnome calendar but it doesn't turn on until manually started.  I have searched for a solution and found a pile of them.  that being the caswe perhaps somebody knows how to do this or can point me to a solution that works currently?

the reason for this is that while I have appointments I put into google calendar which also turned up on the gnome calendar the notifications didn't go off and I almost missed an apointment.  I think this was because google calendar was not on.  

Thank you.......

---

### Post by DuckHook on 2020-02-14
To turn on any 'buntu app at start, just add it to "Startup Applications". Instructions as follows: [https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html.en](https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html.en)

---

### Post by TheFu on 2020-02-14
It is not possible to start GUI programs that are dependent on a user session login at boot time.

They can be started just after a GUI login, however.  Different DEs have different methods to setup autostart programs just after a GUI login.  It isn't useful to try starting a GUI program for non-GUI sessions, like over ssh, for example.

The difference my seem unimportant today, but trust me, it is absolutely critical to understanding how Unix-like OSes, logins and GU sessions can be bent to our needs.

---

