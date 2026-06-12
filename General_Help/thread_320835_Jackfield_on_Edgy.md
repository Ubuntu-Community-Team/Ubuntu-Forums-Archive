---
title: "Jackfield on Edgy ?"
date: 2006-12-18
forum: General Help
---

### Post by turbojugend_gr on 2006-12-18
Hi all,

**[http://kryogenix.org/code/jackfield/introduction](http://kryogenix.org/code/jackfield/introduction)** have you checked this out?

It is supposed to be able to run apples widgets on ubuntu, it is pre-alpha state, but still the more the testers the better. If anyone managed to run this plz tell me how... share you lucky b****rd! :)

I managed to pull through svn normally, I can't start it though. I get :
```
Traceback (most recent call last):
  File "jackfield/Control.py", line 7, in ?
    import jackfield_dbus
  File "/home/turbojugend/trunk/jackfield/jackfield_dbus.py", line 56, in ?
    raise NotImplementedError("D-Bus "+dbus.version+" untested!")
TypeError: cannot concatenate 'str' and 'tuple' objects

```

Note I have changed the widget location appropriately.

Waiting a reply, best regards TJ.

---

### Post by davedean on 2006-12-18
Just tested it out .. edit jackfield/jackfield_dbus.py, change line #15 to read:

elif minor >= 40 and minor < 400;

and it should start - I found that some widgets won't run as there isnt a full dashboard environment, and it does feel like pre-alpha software.

---

### Post by turbojugend_gr on 2006-12-18
> **davedean said:**
> Just tested it out .. edit jackfield/jackfield_dbus.py, change line #15 to read:

elif minor >= 40 and minor < 400;

and it should start - I found that some widgets won't run as there isnt a full dashboard environment, and it does feel like pre-alpha software.
Yeah it is pre-alpha state, I said so... I t is good to have testers, devs checking it out though (for the time being I 'll sit on the first category). This way it might proceed faster.

Thank you for the reply, I will try it out later on, I suppose it will work,since the dbuse server in edgy is on a later version (52 I guess?).

Best Regards, TJ.

---

