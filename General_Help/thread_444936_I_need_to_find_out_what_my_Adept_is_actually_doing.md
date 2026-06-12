---
title: "I need to find out what my Adept is actually doing now."
date: 2007-05-15
forum: General Help
---

### Post by PerlMountain on 2007-05-15
I had a sort of crash brought on by something related Konqueror while I was installing software.

I had to re-start (accidentally or whatever) and now I want to enable a certain repository and continue my work.

BUT, anything I try to do, it tells me that "Another process is using the packaging system and:
```
You will not be able to change your system settings in any way 
(install, remove or upgrade software), because another process is 
using the packaging system database (probably some other Adept 
application or apt-get or aptitude). Please close the other application 
before using this one.
```

So, I guess the first question is:

Do you think that since the machine was doing work at the time of the crash that it continued where it left off upon restarting services?

Or:
That I need to kill something off and re-do my work.

I don't know if I should just wait and see or if I should try to find out what's going on and kill it off.

Thank you.

---

### Post by PerlMountain on 2007-05-15
Killed it:

```
sudo fuser -vki /var/lib/dpkg/lock;sudo dpkg --configure -a
```

---

