---
title: "Error in gedit"
date: 2007-02-04
forum: General Help
---

### Post by towanda on 2007-02-04
I was attempting to edit my firefoxrc when the following error appeared and all that opened was an empty instance of gedit.  Anyone know how to fix this?  My password was not asked for because I  had just entered it a couple of commands previously.


[color=maroon]towanda@mymachine:~$ gksudo gedit /etc/firefox/firefoxrc

(gedit:21146): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.[/color]

---

### Post by raul_ on 2007-02-04
gksudo always gives that error...i think nobody know why. But apart from the fact that is annoying, it really doesn't affect anything, so don't worry

---

### Post by aysiu on 2007-02-04
The fact that that "error" appears is a bug. Unfortunately, it hasn't been fixed yet...
[https://launchpad.net/ubuntu/+source/gksu/+bug/23917](https://launchpad.net/ubuntu/+source/gksu/+bug/23917)

It's not a real error. Ignore it.

---

