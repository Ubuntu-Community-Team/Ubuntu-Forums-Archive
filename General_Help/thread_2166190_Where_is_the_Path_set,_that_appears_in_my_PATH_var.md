---
title: "Where is the Path set, that appears in my PATH variable?"
date: 2013-08-08
forum: General Help
---

### Post by abraxas334 on 2013-08-08
In what files do generally get Path variables set?

I have a path to some directory in my PATH variable, which I don't understand how it gets added. 
In  none of .bashrc .profile /etc/profile or /etc/bash.bashrc I have a line saying export PATH=/path/to/dir:$PATH, but it appears to be the very first path in the list of added paths. 
It is a custom directory, but I do not remember when I added it or where and I don't know where to look. The fact that it is in the path is not a problem, but I was still wondering how it got there. (It was set in the .bashrc at some point, but I commented that part out, also the .bashrc does not get sourced when I remote loginto the computer)

Thanks for any help, suggestions

---

### Post by Crusty Old Fart on 2013-08-11
I have a similar situation in that part of my PATH variable contains a location for which I haven't been able to discover where it was specified.
So, take the following as a *weak* suggestion.

You might want to take a look in the following places:
[FONT=Verdana]/etc/init.d/rc
/etc/init.d/rc.local
/etc/init.d/skeleton
/etc/init.d/x11-common
[/FONT]/etc/skel/.bashrc
/etc/skel/.profile
[FONT=Verdana]/lib/init/vars.sh[/FONT]
/root/.bashrc
[FONT=Verdana][/FONT]
There must be other places as well since I didn't find what I was looking for in anything listed above.

However, you might get lucky.

Best wishes,

Crusty

---

