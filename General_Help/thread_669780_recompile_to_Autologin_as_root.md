---
title: "recompile to Autologin as root?"
date: 2008-01-16
forum: General Help
---

### Post by quandary on 2008-01-16
Hi!

I'm trying to enable autologin for the user "root". ;-)

I'm already logged in as root, and it worked for over a year now.

Finally, out of convenience, I want to enable autologin. 
It works for a normal user, but when I start gdmsetup, go to the tab security, then click "enable Automatic login" and in the field username type "root", a Message appears saying:
```

USER NOT ALLOWED
Autologin or timed login to the root account is forbidden.

```

I searched Ubuntuforms and google, but so far didn't found a solution.

Then i searched for the source for gdmsetup and found the package "gdm".

So far I managed to get the dependencies for the gdm package, and to compile.

Now i found in /gui/gdmsetup.c the line:
```

				if (user_uid == 0 || user_uid < GdmMinimalUID) {
					/* we can't accept users that have uid lower
					   than minimal uid, or uid = 0 (root) */

```

---

