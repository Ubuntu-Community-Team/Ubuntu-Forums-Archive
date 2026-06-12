---
title: "sudo apps without password prompt"
date: 2007-04-24
forum: General Help
---

### Post by Aetherius on 2007-04-24
Hey,

Just wondering if anyone could remind me where you declare that an app doesn't need a password to be run as root. I know it possible because I did it on my old MythTV box so that the HID daemon was run whenever I logged in. (so my phone was a bluetooth remote).

The problem is that i have a script being called in .bash_profile and I need it to do a few root actions, and I don't want to be entering my password twice everytime i log in.

Aeth

---

### Post by sisco311 on 2007-04-24
open a terminal:
```
sudo visudo
```
> **your_user_name** ALL=NOPASSWD:**/usr/bin/application -opton**
save: Ctrl+o Enter 
exit:  Ctrl+x

---

### Post by Aetherius on 2007-04-24
yup, thats the begger, cheers

---

### Post by schmolch on 2007-04-25
I would like to run "s2ram -f -a3" from a panel-launcher, but i cant get it working.

I tried 
"sascha ALL=NOPASSWD:/sbin/s2ram" and 
"sascha ALL=NOPASSWD:/sbin/s2ram -f -a3" and 
"sascha ALL=NOPASSWD:/sbin/s2ram -opton"  (whats opton?)
but they all return they same errors you get without root privileges.

Any idea?

---

### Post by Pauan on 2008-05-27
> **schmolch said:**
> I would like to run "s2ram -f -a3" from a panel-launcher, but i cant get it working.

I tried 
"sascha ALL=NOPASSWD:/sbin/s2ram" and 
"sascha ALL=NOPASSWD:/sbin/s2ram -f -a3" and 
"sascha ALL=NOPASSWD:/sbin/s2ram -opton"  (whats opton?)
but they all return they same errors you get without root privileges.

Any idea?
I'm not sure why, but it won't let you run sbin applications. "/usr/bin" works ok for me, but "/usr/sbin" doesn't..

---

### Post by kerry_s on 2008-05-27
there should be a gap/space:
sascha ALL=NOPASSWD:/sbin/s2ram
to 
sascha ALL=NOPASSWD: /sbin/s2ram

mine->

---

