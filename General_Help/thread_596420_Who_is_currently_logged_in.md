---
title: "Who is currently logged in?"
date: 2007-10-29
forum: General Help
---

### Post by jshurst on 2007-10-29
I've looked for this but can't seem to find it (probably been asked a lot), but how do I tell who is currently logged onto the computer?  For example if I'm logged in remotely and my roommate is logged on locally?  In Windows I can open the task manager and go to the "Users" tab (at least in Server 2003 I can).

Can someone tell me how do find this out?

Thanks,

Jeremy

---

### Post by stoodleysnow on 2007-10-29
If you're using Gutsy it should say who's logged in next to the network and search icons in the top right corner.:)

---

### Post by jshurst on 2007-10-29
Thanks, but I'm talking about for multiple users.  I see that I am logged in and I believe that the drop down is for fast user switching, but I want to know the sessions.

I'm coming from Windows (although dabbling with Ubuntu since Breezy) but I can see who is logged on and a session id.  So for example, let's say that I log on using remote desktop and then someone else logs on to the physical machine I can open the task manager and see that there are two sessions currently running.  I can then send a message or kick them off.  Or if I'm logged on in two places then each of my accounts will have a different ID.  Basically I want to make sure that no one unexpected is accessing my computer (via a remote client or ssh, etc).

There has to be something like that for linux right?

Thanks though,

J

---

### Post by taurus on 2007-10-29
```
finger
```

---

### Post by jshurst on 2007-10-29
That will do, thanks a lot!

J

---

### Post by scorp123 on 2007-10-29
Other commands you might be interested in:

**who** ... similar to "finger" above, lists all users currently in the system.
**last** ... see the login/logout history
**lastb** ... see all the bad / failed login attempts
**lastlog** ... when was the last time somebody logged into the system?

---

