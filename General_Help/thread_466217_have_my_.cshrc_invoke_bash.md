---
title: "have my .cshrc invoke bash"
date: 2007-06-06
forum: General Help
---

### Post by mattie_linux on 2007-06-06
hello.
please excuse my English.

I want to use bash as much as possible. But instead of changing my default shell in my (networked at a server) /etc/passwd, because not all my machines have bash, I want to *csh* as my default shell and do this:

Have my .cshrc to *check* for bash, and then if it exists, invoke it.
I am  kind of a newbie. Can somebody tell me if this is possible?

thanks you,
Mattie

---

### Post by taurus on 2007-06-06
If you want to use csh as your default shell, why not make it your default shell like

```
chsh
```

---

### Post by mattie_linux on 2007-06-06
Hi there Taurus. 
Thanks so much for the reply!
I actually don't want to change it at the (networked) passwd level, because some of my machines don't have bash.  I want my .cshrc to check for the presence of bash, and if it is there, run it.

---

### Post by pmg on 2007-06-07
You don't want to do it in your .cshrc, because then if you happen to run a (t)csh shell script that sources it the shell'll go off to bash-land and not do what it's supposed to do.  When (t)csh is the login shell, it also sources ~/.login - which migh be a reasonable place to start a bash shell.  The csh to test /bin/bash for execute access and if so exec it is:
```
if ( -x /bin/bash ) exec /bin/bash -l
```
however I suggest you proceed with caution.  If you mess up your .login you may not be able to login.  Make sure you have a way to test it and back it out if it doesn't work.

---

### Post by Mr. C. on 2007-06-07
Save yourself the headache.  Either:

 a) install bash on all systems so that you can simplify your tasks
 b) change your local passwd entry to use bash
 c) create yourself a simple csh alias like "gobash" which you type once you login, or simply type "exec bash".

You will find that trying to live in the two shell variants (sh/csh) becomes tiresome.

You can create an /etc/passwd entry on any local machine, and that entry can be used before the network (eg. NIS) entry. 

MrC

---

