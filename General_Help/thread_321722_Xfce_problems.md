---
title: "Xfce problems"
date: 2006-12-19
forum: General Help
---

### Post by Korben_Dallas on 2006-12-19
Hi,

I'm using Xubuntu and I was trying to get PCSC working and I'm not sure what happened but at some point the menus and desktop disappeared. I was left with my open Terminal windows.

In the login screen, no matter what session I choose the problem still remains.

What is the problem? I can load parts of Xfce with commands but is there a way to "reset" back to the default?

I've loaded parts of Xfce - xfce4-panel and xfce-session... am I missing some?

After I start xfce4-panel I get the menus back but if I close the terminal window or press Ctrl+C they go away again. The Terminal window shows:

(xfce4-panel:4261): CRITICAL **: An item was unexpectedly removed: "Trash Applet".

Even still when I restart and log back I still have the 2 terminal windows... what's up with this? how can I delete this "session settings"?

Shouldn't a restart take care of restarting the services (jobs in linux?).

As you might have guessed I'm new to Linux :confused:

---

### Post by Korben_Dallas on 2006-12-19
Used Alt+F2 and was able to run the necessary xfce modules. Reinstalled packages and restarted saving the session.

Seems to be working ok now :)

---

