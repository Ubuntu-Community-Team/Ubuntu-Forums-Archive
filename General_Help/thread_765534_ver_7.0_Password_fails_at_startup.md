---
title: "ver 7.0 Password fails at startup"
date: 2008-04-24
forum: General Help
---

### Post by MrTaiko on 2008-04-24
Ubuntu does not recognize my logon password.  Some attempts will display the password as readable characters.  Other attempts will mask the characters.  In either case, I cannot logon to the system.

Is there any way to correct this short of a total reinstall of Ubuntu?

---

### Post by Archimedes0212 on 2008-07-24
if you go into recovery mode it can be fixed

login to an account that works (hopefully you have one -- root maybe).  Then you just need this command: pwd [user]  where [user] is replaced by the username.  You will then be prompted for a new password.  Follow the prompts, restart and voila, it should be working

---

