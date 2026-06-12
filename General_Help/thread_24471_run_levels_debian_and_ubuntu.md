---
title: "run levels debian and ubuntu"
date: 2005-04-07
forum: General Help
---

### Post by jimbob@ubu on 2005-04-07
Hi,

I hope stumper doesn't mean no one looks at these questions ;-)

Anyway one thing I can't figure out in debian or ubuntu is how I can change my run level policy so that an apt-get upgrade doesn't blow away the symlinks I have configured using update-rc.d.  

For example I set all all runlevels to stop on the http server on my desktop and only start it when I need via /etc/init.d/http start.  But after an apt-get upgrade all the default start symlinks are back.  

thanks

---

### Post by soul_rebel on 2005-04-07
You don't have to stop services at all runlevel! Simply don't make it start. I have customized run levels but i am not getting any change by upgrades.

---

### Post by jimbob@ubu on 2005-04-11
Thanks soul_rebel but how do you not start it ?

remove the start up script all together ? (I think that would break the .deb)

thanks

James

---

### Post by bobbyc on 2005-04-11
install sysvconfig or sysv-rc-conf and you should be set.
They are both console menu driven.  

BTW, the  default runlevel for the graphical logon is 2.

---

### Post by Gandalf on 2005-04-11
try this:
```

update-rc.d <script_name> start 20 3 4 5 . stop 20 0 1 2 6

```
where <script_name> is the file name located in /etc/init.d

this will add <script_name> to run on levels 3, 4, and 5 and remove it (make i stop not start) in runlevels 0, 1, 2 and 6

---

