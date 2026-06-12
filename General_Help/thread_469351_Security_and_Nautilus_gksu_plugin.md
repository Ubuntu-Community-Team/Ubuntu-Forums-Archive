---
title: "Security and Nautilus gksu plugin?"
date: 2007-06-09
forum: General Help
---

### Post by ThinkBuntu on 2007-06-09
I installed the Nautilus gksu (open as administrator from context menu) plugin. Now, I can right-click and open any file on my computer, and it never prompts me for a password. Why doesn't it prompt for a password? It's very useful and time-saving, but I can't have it around if it's this lax.

---

### Post by ThinkBuntu on 2007-06-10
bump

---

### Post by DoktorSeven on 2007-06-10
Probably sudo's timeout still in effect; if you enter your password for sudo once, it'll remember your authentication and not ask for passwords for a while longer.

I don't like this, so I changed how sudo worked:

**VISUAL=/usr/bin/gedit sudo visudo**

Add **timestamp_timeout=0** to the end of the Defaults line as so:

**Defaults	!lecture,tty_tickets,!fqdn,timestamp_timeout=0**

Now it should ask for a password every time, as it should in my view :).  This made the nautilus Administrator menu entry ask for a password every time for me. (If you just want to lower the timeout, replace 0 with the number of minutes you want the timeout to be.)

---

