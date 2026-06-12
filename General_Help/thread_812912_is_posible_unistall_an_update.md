---
title: "is posible unistall an update?"
date: 2008-05-30
forum: General Help
---

### Post by d2ortiz on 2008-05-30
I want to unistall the hardy's may 30, 2008 update. is this possible ?

The problem is, after the update i can't write in Evolution without the windows goes dark and freeze.

Before the freeze the editing speed is very slow and after few keystroke the programs hangs.

Selecting from address books a few names with mouse have the same effects.


thanks in advance,
Dennis

---

### Post by zvacet on 2008-05-30
Synaptic>file tab>history and there you will see what you installed on that date.

```
sudo aptitude forbid-version packagename
```

---

### Post by unutbu on 2008-05-30
I think you can downgrade a package with this command
```
sudo apt-get -f install packagename=versionnumber
```

but I have never tried this and I've been warned it can break a system. :(

---

