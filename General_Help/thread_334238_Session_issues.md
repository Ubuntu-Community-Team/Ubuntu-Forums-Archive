---
title: "Session issues"
date: 2007-01-08
forum: General Help
---

### Post by Georgio_1999 on 2007-01-08
Hi guys,

Having a few problems since I tried out beryl & xgl.  It seemed a little slow for my machine so I reverted to the normal setup.  Now when I boot up I get an error box "Error activating XKB configuration".  I think this is something to do with the keyboard settings which I had to change when I changed display manager.  Additionally when I go system->quit I get a popup saying "Session saved ok".  This closes a few windows and I have to go system->quit again.  This brings me back to gdm where I can shutdown from (before i could do a straight shutdown from gnome).  Any ideas what this is and how to fix it?  Linked to that, my sessions  aren't saving properly so when I reload I don't get every window back (even if just a few terminals and gedit, although I will get some of them).  Failing a fix anyone know how to roll back to default configuration?  I know you can do this using apt somehow.  I'm running dapper btw.

Thanks in advance for any pointers,

George

---

### Post by dcstar on 2007-01-08
> **Georgio_1999 said:**
> Hi guys,

Having a few problems since I tried out beryl & xgl.  It seemed a little slow for my machine so I reverted to the normal setup.  Now when I boot up I get an error box "Error activating XKB configuration".  I think this is something to do with the keyboard settings which I had to change when I changed display manager.  Additionally when I go system->quit I get a popup saying "Session saved ok".  This closes a few windows and I have to go system->quit again.  This brings me back to gdm where I can shutdown from (before i could do a straight shutdown from gnome).  Any ideas what this is and how to fix it?  Linked to that, my sessions  aren't saving properly so when I reload I don't get every window back (even if just a few terminals and gedit, although I will get some of them).  Failing a fix anyone know how to roll back to default configuration?  I know you can do this using apt somehow.  I'm running dapper btw.

Thanks in advance for any pointers,

George

You may want to try creating a new user account, and then logging in under it and seeing if the problems remain.

If they are not there with the new account, then possibly some permissions/settings in your original account have changed. If that is the case, you may be able to delete/replace some files in your original account to get things back to normal.

---

