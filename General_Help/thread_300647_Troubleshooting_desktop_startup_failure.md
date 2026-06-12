---
title: "Troubleshooting desktop startup failure"
date: 2006-11-16
forum: General Help
---

### Post by elian on 2006-11-16
Hi,

I've got a user with no admin privileges using Dapper Drake. She's been using it uneventfully for a few days. Today, on logging in the desktop fails to load, meaning that she is left staring at the background + the spinning cursor, but nothing else. AFAIK all other services have started.

The machine is several hundred miles from me, so I'm looking for ideas as to what might have happened, and how I can fix the problem  (assuming I can get access to it remotely, or by flying there).

Thanks!

---

### Post by elian on 2006-11-16
Just to provide more details, after login, the keyboard is dead, but the mouse still responds.

---

### Post by PartickThistle on 2006-11-16
**Ctrl-Alt-F1** and make sure **x-session-manager** is running.

---

### Post by elian on 2006-11-16
x-session-manager doesn't appear to be running. What could the user have done to have caused this kind of problem? She has no admin rights at all!

---

### Post by PartickThistle on 2006-11-16
In my past experience, I've found having it start once, managing to log-in and ensuring **Ask On Logout** & **Automatically Save Changes to Session** makes it work upon re-login within System->Session.

Sorry I can't be more help.  

Give that a shot (if you can) and let me know if it works.  If not, I'll think of something else.

---

