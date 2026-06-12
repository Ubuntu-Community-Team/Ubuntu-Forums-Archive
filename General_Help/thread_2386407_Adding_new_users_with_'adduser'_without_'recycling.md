---
title: "Adding new users with 'adduser' without 'recycling' of older unused UIDs"
date: 2018-03-05
forum: General Help
---

### Post by chuckster-pl on 2018-03-05
Hi,
I used to work with 'adduser' script on Slackware and there it works without 'recycling' of older unused UIDs. Now I want to move on Ubuntu 16.04 LTS, but here script 'adduser' works different - it 'recycle' unused UIDs (UIDs from users that have been deleted earlier).

Attachments:
[ATTACH]278810[/ATTACH]
[ATTACH]278811[/ATTACH]

Is it possible in Ubuntu to get 'adduser' without 'recycling' of older unused UIDs?

---

### Post by TheFu on 2018-03-05
The manpage says:```

       -u, --uid UID
           The numerical value of the user's ID. This value must be unique, unless the -o option
           is used. The value must be non-negative. The default is to use the smallest ID value
           greater than or equal to UID_MIN and greater than every other user.
```
So it appears your setup/script is doing something different than the default.

There are config files (adduser.conf and few others). The -K option might be helpful.  

Plus, there is the useradd tool, which is lower level - it has a useradd.conf file and supports scripting, according to the manpages.  It shouldn't be hard to specify the desired UID after using getent passwd to find the largest current uid.  I haven't done this. We use LDAP.

---

