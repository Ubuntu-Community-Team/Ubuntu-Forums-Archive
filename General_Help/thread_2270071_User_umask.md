---
title: "User umask"
date: 2015-03-20
forum: General Help
---

### Post by dtomas2 on 2015-03-20
Hello.
I'm running ubuntu 3.13.0-32.

I find the ***root*** default umask, 022, at /etc/login.defs
The ***user*** umak is 002 but I can not find where this is defined.

I've looked into the follwing locations but found nothing:
[LIST]
[*]/etc/profile
[*]/etc/bash.bashrc
[*]~/.bashrc
[/LIST]

Did some one found it?

Thank you.

---

### Post by dino99 on 2015-03-20
you'd better stay with the ubuntu default value, and not trying to tweak then breaking the system

---

### Post by dtomas2 on 2015-03-20
Knowing where the default value is defined doen's necessary mean I will change it.
If I can see the root umask I should be able to see the user umask also.

---

### Post by bab1 on 2015-03-20
> **dtomas2 said:**
> Hello.
I'm running ubuntu 3.13.0-32.

I find the ***root*** default umask, 022, at /etc/login.defs
The ***user*** umak is 002 but I can not find where this is defined.

I've looked into the follwing locations but found nothing:
[LIST]
[*]/etc/profile
[*]/etc/bash.bashrc
[*]~/.bashrc
[/LIST]

Did some one found it?

Thank you.
The first two locations are global (all users)
The Third location is local to the user logged in.   The proper place to declare a specific user umask is either the .profile or .bash_profile file.

The umask is always the last value set.  You can set the umask value in a script, if you wanted to, so the use would be only with that script.  There is no reason to set the umask for any user (root or mortal) other than their  defaults.  If you need to change the umask for a *specific* reason you should do that via the process script.  In fact a terminal session works the same way.  Open a terminal session and declare these three commands```
cd
umask 077
touch umask.test
```...then check the permissions on the file *umask.test*.  When you close the terminal that umask setting goes away.

To see HOW the default umask is set read the specific umask man page```
man 2 umask
```

Is this just a "why is it like that" question, or do you have a specific problem or need?

---

