---
title: "Application Scope Env Variables?"
date: 2005-04-29
forum: General Help
---

### Post by Eproxus on 2005-04-29
Is it possible to set environment variables for specific applications?

The case in question is Gaim were I want to use a different dictionary. The dictionary is set by the Debian env variable $LANG which also sets the user interface language. I still want english in my user interface but swedish spelling in Gaim. Is this acomplishable? The only way I can think of is to fake the $LANG variable for Gaim only...

Thanks in advance! / Adam

---

### Post by odix on 2005-04-29
Try to start gaim like this:
```
LANG="<locale>" gaim
```

or write a little script
```
#!/bin/bash
export LANG="<locale>"
/usr/bin/gaim
exit 0
```
I don't know the locale for sweden, sorry

odiX

---

### Post by Eproxus on 2005-04-29
Got it working!

.startgaim.sh
```
LANG=sv_SE
gaim
```

Thanks!

---

