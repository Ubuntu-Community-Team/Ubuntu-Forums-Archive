---
title: "update manager offers me an inferior version of gaim"
date: 2007-04-20
forum: General Help
---

### Post by jfca283 on 2007-04-20
i installed gaim 2.0 beta 6 running a script in dapper
but the update manager shows me an update of gaim to the beta 5
why is that?
how do i resolve it?
it isn't comfortable see the icon alerting me of an update that i don't need
well, that's all
thanks for your posts
bye

---

### Post by Brucevdk on 2007-04-21
The script you used most likely just extracted some files and didn't actually use the package manager, because of this the package manager doesn't know you have beta 6 installed. If you were/are using Dapper the latest available version was probably beta 3, so for the package manager beta 5 is an update.

Personally I'd just do this:

1) Remove gaim from the package manager, this will most likely undo everything your script did.

```
sudo apt-get remove gaim
```

2) Add a third party repository that actually contains beta 6. Create a file called *debuntu.list* in */etc/apt/sources.list.d/* which contains (replace *dapper* if needed):
```

deb  http://repository.debuntu.org/ dapper multiverse
deb-src http://repository.debuntu.org/ dapper multiverse

```

You could also add the lines to */etc/apt/sources.list* as mentioned in [the instructions]("http://repository.debuntu.org/#howtouse")

3) Execute:
```
sudo apt-get update
```

Your package manager should now offer to install beta 6.

---

### Post by jfca283 on 2007-04-21
the beta 5 is on debuntu, not the beta 6

---

