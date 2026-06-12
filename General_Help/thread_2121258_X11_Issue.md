---
title: "X11 Issue"
date: 2013-03-01
forum: General Help
---

### Post by cbo0485 on 2013-03-01
I am running Ubunto 12.10 on a desktop, and am trying to connect to an AIX server to use X.  When I ssh to the server, I do 'ssh -Y <hostname>'.  As my user id(id matches between ubuntu client desktop and AIX server), I can do xclock.  But in order to do what I need to do, I need to su to a different user id on the AIX server.  Whenever I do that, and run xclock, I always get:

X11 connection rejected because of wrong authentication.
X connection to localhost:10.0 broken (explicit kill or server shutdown).


Version info of client:
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.10
Release:	12.10
Codename:	quantal

---

### Post by matt_symes on 2013-03-01
Hi

> **cbo0485 said:**
> I am running Ubunto 12.10 on a desktop, and am trying to connect to an AIX server to use X.  When I ssh to the server, I do 'ssh -Y <hostname>'.  As my user id(id matches between ubuntu client desktop and AIX server), I can do xclock.  But in order to do what I need to do, I need to su to a different user id on the AIX server.  Whenever I do that, and run xclock, I always get:

X11 connection rejected because of wrong authentication.
X connection to localhost:10.0 broken (explicit kill or server shutdown).


Version info of client:
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.10
Release:    12.10
Codename:    quantal

This is due to X11 cookies. When you login your coockies match but when you su <user> the cookies don't match and the X server kills the connection to you.

You need to ensure that the user you are su'ing to has the same cookie you are using.

Try this

when you connect and before you su to the new user

From the terminal type

```
xauth list $DISPLAY
```

This will list your current secret cookie that your X client and the X server share to authenticate.

Here is mine (slightly edited)

```
matthew-S206:/home/matthew % xauth list $DISPLAY
matthew-S206/unix:0  MIT-MAGIC-COOKIE-1  52829xxxxxxxxxx51fab2e2abddfb26d
matthew-S206:/home/matthew % 

```

You then need to ensure that the user you are su'ing to will use the same cookie as you. 

xauth should do this for you

```
xauth add <cookie details>
``` 

On my system it wouold be

```
xauth add matthew-S206/unix:0  MIT-MAGIC-COOKIE-1  52829xxxxxxxxxx51fab2e2abddfb26d
```

Which is basically "xauth add" and a copy and paste of the cookie details returned from xauth list $DISPLAY.

Then try su'ing to the new user.

Post back on efficacy as this is an AIX box.

Kind regards

---

### Post by cbo0485 on 2013-03-04
Worked.  Thanks for the help.  Never would have found that

---

