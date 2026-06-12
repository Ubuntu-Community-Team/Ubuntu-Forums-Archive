---
title: "this is how to login as root in the desktop gui"
date: 2007-04-21
forum: General Help
---

### Post by sdowney717 on 2007-04-21
you can activate a root login!
click on system-administration-login window
select the security tab
click on 'allow local system admin login'

THEN click system-administration-users and groups
click root
click preferences
set a new password

click ok

you can now login with root

---

### Post by nsleiman on 2007-04-21
Nice to know :) eventhough i dont think its a must, its more secure to log in as user and sudo whatever you want.

what are the benefits logging in as super user ?

---

### Post by mickbuntu on 2007-04-21
Thanks for the info like the user above but any implications? for opening an operating system hole.

> **sdowney717 said:**
> you can activate a root login!
click on system-administration-login window
select the security tab
click on 'allow local system admin login'

THEN click system-administration-users and groups
click root
click preferences
set a new password

click ok

you can now login with root

---

### Post by sdowney717 on 2007-04-21
I wanted to click files open to edit some files  which I could not do as a regular user.
I am also used to having a root login from other versions of linux.
I can understand why ubuntu does not enable this by default but for me it is inconvenient.

---

### Post by Zuuswa on 2007-04-21
If you really want to use gui for modifying system files, then do something like sudo nautilus or sudo thunar, or whatever file manager you use.  Then you can navigate using a file manager in root mode, and open files etc. in root mode.  Its still alot safer then enabling root account.

---

### Post by nsleiman on 2007-04-21
I agree with the above reply,
sudo is a very powerful command and allows you everything.

be careful with this command you can always harm your system :) (kidding)

---

### Post by rich.bradshaw on 2007-04-21
yeah, just sudo nautilus, don't do it this way kids.

---

### Post by taurus on 2007-04-21
> **sdowney717 said:**
> I wanted to click files open to edit some files  which I could not do as a regular user.
I am also used to having a root login from other versions of linux.
I can understand why ubuntu does not enable this by default but for me it is inconvenient.

Perhaps you need to read this.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

