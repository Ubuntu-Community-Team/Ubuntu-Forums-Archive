---
title: "/bin/sh -&gt; /bin/dash"
date: 2008-01-16
forum: General Help
---

### Post by NGSG on 2008-01-16
hi,
I need to install a software which uses bash and makes heavy use of /bin/sh.
I could see that /bin/sh is a symbolic link to /bin/dash. I changed it to point to /bin/bash.
Could this  somehow break some of the Ubuntu modules which use dash (relying on the fact that it's dash indeed) instead of bash?
thanks.

---

### Post by luisromangz on 2008-01-16
There shouldn't be scripts dependant on features of dash that won't exist in bash, mainly because dash is simpler and have fewer features (so it's faster) than bash.

---

### Post by mcduck on 2008-01-16
> **luisromangz said:**
> There shouldn't be scripts dependant on features of dash that won't exist in bash, mainly because dash is simpler and have fewer features (so it's faster) than bash.You are thinking about this in the wrong way. The scripts are using features of Bash that are not available in Dash.. ;)

Anyway, I recommend just editing those scripts, changing the "#! /bin/sh" on the first line into "#! /bin/bash".

If the scripts rely on features only available in Bash, they should also tell the system to use Bash, not the default shell (whichever that happens to be).

Also, changing your default shell from Dash to Bash will quite like make your system slower, as Bash is heavier than Dash is.  Otherwise it will of course work, Bash supports all features available in Dash.

---

