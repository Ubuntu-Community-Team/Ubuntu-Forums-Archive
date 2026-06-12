---
title: "Ubuntu 14.04 and LDAP login problems - anyway to refresh contents of .config dirs?"
date: 2015-11-18
forum: General Help
---

### Post by morphyrichards1 on 2015-11-18
Hi, I have an Ubuntu (Actually Edubuntu) network. Logins are handled by an LDAP server (Zentyal) set-up as in this thread [https://forum.zentyal.org/index.php?topic=12925.0](https://forum.zentyal.org/index.php?topic=12925.0)

This mostly works but intermittently the login hangs when a user tries to login. IE. the login box disappears and it just hangs on the background picture without the desktop appearing.
This is happening frequently to assorted users, I don’t know what triggers it.
 
I have discovered through trial and error that removing either one particular (not sure which one) or all of the contents of these directories for affected users solves the problem. That is to say the user can then login again.
.cache
.config
.compiz
.gconf
.local (on further reflection I probably don’t want to be deleting this one)

Is there any neat way I can do a 'refresh' on every users .config directories when they log out and then apply this to all users? Or would I be better off writing a script to recursively delete these folders at night with chron or .. something better?

---

