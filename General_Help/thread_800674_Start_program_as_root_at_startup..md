---
title: "Start program as root at startup."
date: 2008-05-20
forum: General Help
---

### Post by lynxus on 2008-05-20
OK, ive created a new app in sessions so it starts on login ( Loads truecrypt )
However the app needs root, How do i get it to grab for root? IE: asks for a password?

A bit like how the keyring manager grabs for a password etc.


Any help would be great

Thanks
-G

---

### Post by sdennie on 2008-05-20
You should be able to prefix the command in Sessions with gksudo.  So:

```

gksudo truecrypt

```

---

