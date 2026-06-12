---
title: "Tell what user is being logged in from /usr/share/xsessions?"
date: 2013-07-16
forum: General Help
---

### Post by Jalaska13 on 2013-07-16
I want to have a setup so that each user can have a custom user-specific pre-login script. What I have so far:

/usr/loca/bin/session-wrapper.sh - a script which looks in the current user's home folder for a ".prelogin.sh" script, and executes it if possible before executing the proper x session.
/home/<user>/.prelogin.sh - a script which does pre-login tasks (whatever the user may want).

In the config files in /usr/share/xsessions, I've set up the x sessions to call /usr/local/bin/session-wrapper.sh.

This works properly, except for one caveat: session-wrapper.sh is not being called as the target user, so I don't know what user is being logged in, and thus I don't know which user's .prelogin.sh script to execute. Does anybody know if there's a way that I can figure out in the script (or perhaps in the xsession config files) what user is being logged in?

Thanks!
Josh

---

### Post by dino99 on 2013-07-16
have you glanced at [https://wiki.ubuntu.com/CustomXSession](https://wiki.ubuntu.com/CustomXSession) ?

---

### Post by Jalaska13 on 2013-07-16
Oh, cool; I somehow didn't come across that. That answers literally all of my questions. Thanks!

---

### Post by oldos2er on 2013-07-16
Moved to General Help.

---

