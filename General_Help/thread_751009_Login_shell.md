---
title: "Login shell"
date: 2008-04-10
forum: General Help
---

### Post by pnmoslo on 2008-04-10
Can anyone help with a minor problem?

Ubuntu server -- all logins have started to default to /bin/sh instead of the shell specified per user in /etc/passwd (usually bash for real users).

All bash files are present -- typing bash at the prompt brings up bash and everything functions perfectly. Not a big problem (except that rm is aliased to rm -iv in the bash files), but I simply don't understand why this isn't working. Only possible thought is file permissions -- is bash picky about this (though I can't see anything that isn't standard).

---

### Post by brian_p on 2008-04-10
> **pnmoslo said:**
> Can anyone help with a minor problem?

Ubuntu server -- all logins have started to default to /bin/sh instead of the shell specified per user in /etc/passwd (usually bash for real users).

All bash files are present -- typing bash at the prompt brings up bash and everything functions perfectly. Not a big problem (except that rm is aliased to rm -iv in the bash files), but I simply don't understand why this isn't working. Only possible thought is file permissions -- is bash picky about this (though I can't see anything that isn't standard).

[http://www.debian-administration.org/articles/231](http://www.debian-administration.org/articles/231)

---

### Post by pnmoslo on 2008-04-10
Well, yes, that's how it's supposed to work. But it doesn't -- the shell listed in /etc/passwd, whatever it might have been correctly changed to by chsh, is not getting picked up at login -- all users default to /bin/sh

---

### Post by brian_p on 2008-04-10
> **pnmoslo said:**
> Well, yes, that's how it's supposed to work. But it doesn't -- the shell listed in /etc/passwd, whatever it might have been correctly changed to by chsh, is not getting picked up at login -- all users default to /bin/sh

Some ideas:

bash is listed in /etc/shells?

Read man chsh. Change the shell of a particular user.

```
chsh <username>
```

Log out and log in again.

---

### Post by pnmoslo on 2008-04-10
Yes and yes. Even a new user turns up in /etc/passwd with /bin/bash, but gets /bin/sh on login. There must be something in the login scripts which is either not picking up the required shell info, or is refusing it. Can't find anything in the logs.

---

### Post by brian_p on 2008-04-10
> **pnmoslo said:**
> Yes and yes. Even a new user turns up in /etc/passwd with /bin/bash, but gets /bin/sh on login. There must be something in the login scripts which is either not picking up the required shell info, or is refusing it. Can't find anything in the logs.

Some final thoughts:

```
echo $SHELL and echo $BASH
```

both return /bin/sh I suppose.

/etc/profile hasn't been altered? I expect not.

Any /home/username/.profile?

---

### Post by brian_p on 2008-04-10
> **pnmoslo said:**
> Yes and yes. Even a new user turns up in /etc/passwd with /bin/bash, but gets /bin/sh on login. There must be something in the login scripts which is either not picking up the required shell info, or is refusing it. Can't find anything in the logs.

Clutching at straws mode.

The default shell is in /etc/adduser.

You are using adduser not useradd?

---

### Post by pnmoslo on 2008-04-10
Thanks -- that got things moving! A missing .profile file -- so the problem was, as per normal, not exactly what it seemed to be: the shell presumably was bash, but because .bashrc wasn't being read (because of the missing .profile), bash was masquerading as a stripped down shell. 

I've got a bit of fixing to do, but that was definitely the main problem. Thanks for you help.

---

