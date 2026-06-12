---
title: "Hanging Up"
date: 2008-04-03
forum: General Help
---

### Post by philmetz on 2008-04-03
I got linux ubuntu 7.10

Now sometimes, when i click on an application to start it says starting then ends and doenst open. It does it for all applications. Is there someway to fix this?

Also is there like a task manager like windows has that i can access? if so what are the keys?

Thanks

---

### Post by cmnorton on 2008-04-03
You need to see what's going on -- that is need access to error messages -- and we need to know more information to help you. 

Is this an x-term application or graphically based? 

Did you write the application or did it come with Ubuntu?

For now, right after this behavior happens, try entering these commands

sudo tail /var/log messages
sudo tail /var/log/syslog

and see if anything shows up there to give you a clue.

If this were an application you could run in an x-term, the launcher gives you that ability, and you could at least see errors that way, too.

I

---

### Post by prshah on 2008-04-03
> **philmetz said:**
> when i click on an application to start it says starting then ends and doenst open. It does it for all applications. Is there someway to fix this?

Also is there like a task manager like windows has that i can access? if so what are the keys?


You can use the System-Administration-System Monitor to see running processes and much more information, just like XP's task manager.

To debug the reason for your application failing to load, open a terminal (Applications-Accessories-Terminal) and then try to run the application you want, eg ```
gedit
``` then copy and paste any error messages.

---

