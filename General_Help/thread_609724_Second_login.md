---
title: "Second login"
date: 2007-11-11
forum: General Help
---

### Post by apoth on 2007-11-11
I used to have a menu option for a new login in a nested window - it's not there anymore, does anyone know how I can get it back?

Anyway, I believe the command it runs is gdmflexiserver -xnest but running that produces the following output:

```
gdmflexiserver[27158]: WARNING: Unable to open a display

```

and then just returns.

Also, clicking the log out button and switch user, then entering details for a different user account just shows me the ubuntu brown desktop background.

Anyone know how I can get around these? Thanks.

---

### Post by rhipwell on 2007-11-12
I have noticed the same thing. So far no luck. I'll post if I find anything...

---

### Post by rhipwell on 2007-11-12
[SOLVED]

command is 

gdmflexiserver --xnest

---

