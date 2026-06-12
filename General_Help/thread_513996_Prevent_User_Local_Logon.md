---
title: "Prevent User Local Logon???"
date: 2007-07-31
forum: General Help
---

### Post by Nortonw on 2007-07-31
How can I prevent a user from loging on locally to the machine??

I have an Ubuntu VMWare Server and I want to enable an account for people to use the vmware remotely but not be able to logon to the ubuntu host server.

How can I do this?

I basically dont want them to be able to do anything other than use the vmware remotely.


Thanks

---

### Post by Nortonw on 2007-08-01
Bump

Anyone ????????????

---

### Post by Shib on 2007-08-01
in /etc/passwd edit their lines from something like this:

adam:x:1000:1000:adam,,,:/home/adam:/bin/bash

to something like this:

adam:x:1000:1000:adam,,,:/home/adam:/bin/false

then they can't get a local shell, which is I think what you mean.

---

### Post by nitro_n2o on 2007-08-01
> **Shib said:**
> in /etc/passwd edit their lines from something like this:

adam:x:1000:1000:adam,,,:/home/adam:/bin/bash

to something like this:

adam:x:1000:1000:adam,,,:/home/adam:/bin/false

then they can't get a local shell, which is I think what you mean.

before doing this you should ```
echo /bin/false > /etc/shells 
``` i'm not sure if that will work though.. maybe i don't know give it a shot

---

