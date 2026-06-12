---
title: "Can't rename /bin/uname"
date: 2013-01-04
forum: General Help
---

### Post by professorYaffle on 2013-01-04
A few months ago, on an Oneiric desktop machine, we were trying to persuade a recalcitrant piece of third party software to install, and had to fool it's installer by moving /bin/uname to /bin/uname.orig and replacing it with a script that told it the lies the installer wanted to hear.

Forgot to repair uname afterwards and just noticed it was still bodged before the Christmas hols. However, I can't revert that change. Whenever I try to remove or rename /bin/uname I get this error message: "rm: cannot remove `uname': Operation not permitted".  Not even if I take the machine down to single user mode.

Anyone know what's causing this error, and how to bypass it? (All I want to do is revert things with: mv /bin/uname.orig /bin/uname.)

& what's really confusing me: if something's neurotically protecting uname, how did it get changed to start with?

---

### Post by catalin.vasilescu on 2013-01-04
See who(pid) is using that path "/bin/uname" .

---

### Post by steeldriver on 2013-01-04
maybe the file was flagged immutable (with chattr) at some point - what does

```
lsattr /bin/uname
```say?

---

### Post by professorYaffle on 2013-01-04
Mmmm - immutable.

lsattr gives "----i------------e- /bin/uname"

That looks like it's it. Yep - done a "chattr -i" and it's now sorted. (Although I'm still confused as to how it was made immutable to start with - certainly wasn't knowingly done by myself or the sysadmin here.)

---

