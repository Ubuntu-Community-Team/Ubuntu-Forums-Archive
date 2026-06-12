---
title: "This cron job stopped working...please tell me why"
date: 2007-07-08
forum: General Help
---

### Post by harty83 on 2007-07-08
I have a cron job that runs a script I've created that utilizes kwebdesktop.  It used to work until recently I've noticed it no longer works on either my desktop or laptop.

The original cron job was:
```

5 * * * * export DISPLAY=:0 && /usr/bin/web-snapshot

```

But now it does not.  When I added a bit of debug code and have it output it to a text file, I found that I get this error from kwebdesktop:

```

Xlib: connection to ":0.0" refused by server

Xlib: Invalid MIT-MAGIC-COOKIE-1 key

kwebdesktop: cannot connect to X server :0

```

I used to have this problem before I added "export DISPLAY=:0 &&"  but it now seems to have returned for some reason even with the display exported.  Did something change in Feisty to cause this?  Like I said, it has happened on both my laptop and desktop where it used to work without a problem.  I've been using that cron job and script for months now.  It stopped working within the last couple of weeks or so.  

Thanks!
Alan

---

### Post by scxtt on 2007-07-08
what if you try: **5 * * * * export DISPLAY=localhost:0 && /usr/bin/web-snapshot**?

---

### Post by harty83 on 2007-07-08
Then I get:
```
kwebdesktop: cannot connect to X server localhost:0
```

---

### Post by harty83 on 2007-07-08
Okay, so I fixed the problem by running 
```
xhost +
``` 
from the command line. Any clue if I will need to run this every time I start my pc?

---

### Post by scxtt on 2007-07-08
i don't believe it's persistent (b/t reboots @ least or login sessions) ...

---

### Post by harty83 on 2007-07-09
Do you know if there is a way to make it persistent.  Like add hosts or a term for "all" to a certain file or something that will be read each time?  

I've never messed with xhost before.  I understand that it allows/denies hosts to x sessions, correct?

Thanks!

---

### Post by scxtt on 2007-07-09
it may be as simple as adding **xhost +** (or using the full path) to the end of /etc/rc.local ...

yeah, it will allow/deny connections to your X server:
```
DESCRIPTION
       The xhost program is used to add and delete host names or user names to
       the list allowed to make connections to the X server.  In the  case  of
       hosts,  this  provides  a rudimentary form of privacy control and secu-
       rity.  It is only sufficient for a workstation (single  user)  environ-
       ment,  although  it  does  limit  the worst abuses.  Environments which
       require more sophisticated measures  should  implement  the  user-based
       mechanism  or use the hooks in the protocol for passing other authenti-
       cation data to the server.
```

---

