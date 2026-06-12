---
title: "Please help me recover from DUMB mistake"
date: 2007-05-02
forum: General Help
---

### Post by dizzutch on 2007-05-02
So i made a stupid mistake...In my haste while trying to change the owner and group of /var/www to www-data i run 
```

sudo chown -R www-data:www-data *

```
from the /var directory...
Now I am unable to run sudo, since /var/run/sudo is owned by www-data instead of root and I get the following:
```

sudo: /var/run/sudo owned by uid 33, should be uid 0

```
I feel like an idiot, and know I can probably boot with the liveCD, set the permissions back and be happy, but I am currently logged in remotely.

Is there anything I can do, or do i need to wait to get home tonight to boot from liveCD and recover?
Any help is appreciated.

Thanks!

-Dizz

---

### Post by disposable on 2007-05-02
When you have physical access, you can boot into single user mode and fix ownership. Though for all of /var it'll be messy. I don't know of an automated way to rebuild /var. Maybe have a friend tar one up from a working box?

Btw, this is another reason to sudo passwd root.

---

### Post by dizzutch on 2007-05-02
thanks, I'll fix it physically tonight...
believe it or not, as I was changing the permissions, i was thinking "i should really change the root password after this command finishes..."
thanks again.

---

