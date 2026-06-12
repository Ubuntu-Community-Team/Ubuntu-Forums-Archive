---
title: "Default Natilus File"
date: 2007-07-11
forum: General Help
---

### Post by Dashdot on 2007-07-11
So I was using some crap tut that I can't even find now and edited the nautilus file so it would change the usr/bin/nautilus to:

> #!/usr/bin/python

import os, sys

if (not sys.argv[1] or sys.argv[1][0] == '/'):
    os.system('thunar %s' % sys.argv[1])
elif (sys.argv[2][0:7] == 'file://'):
    os.system('thunar %s' % sys.argv[2])
else:
    os.system('nautilus.real %s' % ' '.join(sys.argv[1:]))
#os.system('zenity --info --text="%s"' % ' '.join(sys.argv[1:])) #DEBUG 

Now when I attempt to run nautilus from the debaim menu I get
> Failed to execute child process "/usr/bin/nautilus" (Permission denied)

And.. my icons wont show up on my desktop.

So what is the usr/bin/nautilus file support to be. I'm not the only one using this computer so** I need help ASAP!**
I just want it to be restored. 

Thank you!:)

---

