---
title: "Firefox 2 help - Personal Security Manager"
date: 2006-11-20
forum: General Help
---

### Post by _simon_ on 2006-11-20
I'm using the Firefox 2 that came with Edgy.

I've just tried to view a secure page and got this message:

> 
Unexpected response from server

Firefox doesn't know how to communicate with the server.

    *   Check to make sure your system has the Personal Security Manager
          installed.

    *   This might be due to a non-standard configuration on the server.


I tried the link in Opera and it opens without a problem.

I can't find any reference to a Personal Security Manager in any settings and Google isn't being my friend today.

Any ideas?

EDIT: Tested on another Ubuntu Edgy machine and it worked fine.

Reinstalled firefox from repo - still won't work.
Installed Firefox from Mozilla.com - now it works.

---

### Post by Sukarn on 2006-12-25
I'm having the same problem, though i have to mention that my machine is currently a hybrid build (partially upgraded from dapper to edgy).

I have edgy kernel, nvidia drivers, xserver-xorg, tomboy, mono, firefox, mozilla-thunderbird, but almost everything else is dapper.

I am currently downloading the rest of the updates to complete the dist-upgrade.

---

### Post by catou on 2007-01-29
If it can help anyone, I just had the same problem, i.e. firefox 2.0 would not display https sites. After reading for a while, I decided to try to reinstall libnss3 which is the librairy that is needed to view secure pages. And voilà it worked

---

### Post by loney on 2007-12-20
PSM is available in the mozilla-psm package.

---

