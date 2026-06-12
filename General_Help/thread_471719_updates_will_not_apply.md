---
title: "updates will not apply?"
date: 2007-06-12
forum: General Help
---

### Post by lizzardS on 2007-06-12
hi.
this last set of updates won't seem to apply?  I have tried to check and uncheck various options and it hasn't helped.  Now I am attempting to install Zope and am not seeming to get anywhere again?  Up until Monday this wonderful box ran like a well oiled machine - no problems unless I tried to apt-get something that really shouldn't have been apt-gotted.
Help?

---

### Post by taurus on 2007-06-12
Can you post the output of these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by lizzardS on 2007-06-12
THANK YOU! that absolutely did the trick.  I don't know why I didn't think of it.
the first one didn't work - the second did, then I re-ran the first one.
The system required a restart and it all seems fine now.
I appreciate your help. -liz

---

