---
title: "KMail, ksig and a shell script inbetween"
date: 2007-07-31
forum: General Help
---

### Post by afaflix on 2007-07-31
I get a curious error when I try to get a random sig attached to my e-mail

I have KMail and ksig
In KMail I refer to a small shell script:

sigappend.sh
```

#!/bin/sh
ksig --random
echo ""
echo "                                         Phil"
echo ""

```

The call for the random oneliner is from within the script and I use a bunch of echo tags to regurgitate my personal address and such.

When I open a new mail to be written I get

_**Error - KMail**_
Failed to execute signature script
**sigappend.sh**
Key has expired

:confused: what key ???

anyone know?

running the  ksig --random command directly from KMail works just fine.
the shell script is executable for everyone

---

