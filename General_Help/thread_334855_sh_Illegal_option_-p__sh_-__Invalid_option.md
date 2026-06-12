---
title: "sh: Illegal option -p / sh: - : Invalid option"
date: 2007-01-09
forum: General Help
---

### Post by Ragzouken on 2007-01-09
I was trying to compile something on ubuntu ([Gusanos]("http://gusanos.sourceforge.net/") using scons) and came across the error:
```
sh: Illegal option -p
scons: *** [Console/.build/posix/release/alias.o] Error 2
scons: building terminated because of errors.
```
No-one I knew knew anything about it, so I googled with only a single result: [http://www.ingres.co.uk](http://www.ingres.co.uk) . In there it said:
> For some reason, I have yet to work out, Ubuntu have changed /bin/sh to point to /bin/dash, previously it had been linked to /bin/bash. Since dash is supposed to be POSIX compliant there should be no problem however it does not accept the -p argument pass by ingbuild, resulting in an error:
```

pax failed with exit code
/bin/sh: Illegal option -p

```

Until the Ingres installer is fixed to allow for dash the only solution is to re-link /bin/sh to point to /bin/bash:

sudo mv /bin/sh /bin/sh.orig
sudo ln -s /bin/bash /bin/sh
I followed the instructions and something changed, the error I get is now:
```
sh: - : invalid option
scons: *** [Console/.build/posix/release/alias.o] Error 1
scons: building terminated because of errors.
```
I am wondering if this is related the other error and if anyone knows how to fix this. (I'm running Ubuntu 6.10)

EDIT:
I got it fixed, the problem was I didn't have g++.

---

