---
title: "Need to give Scite permission to save files."
date: 2006-10-19
forum: General Help
---

### Post by Brenlae on 2006-10-19
You see, say I have a simple test file, like so:
```

#include <stdio.h>

int main()
{
    return 0;
}

```
and I name it ctut.c, I can't save it at all - no matter what I name it (blah.c, moo.c, foo.bar).

BUT

If I do sudo scite, it works fine.

So, my question is, how do I give Scite permission to save files in my home dir without having to open it via a sudo command every time?

Thanks in advance. :)

---

### Post by taurus on 2006-10-19
Change permissions so others can write to your home directory!!!

```
chmod 777 /home/your_login_name
```

---

### Post by Brenlae on 2006-10-19
Ok, I just did what you said but it didn't seem to work. Scite is still complaining that it can't save.

Any more ideas?

Thanks. :)

---

### Post by taurus on 2006-10-19
How owns the file right now?  Try something like this then...

```
chmod -R 777 /home/you_login_name
```

---

### Post by Brenlae on 2006-10-19
Just did that and there's no change - still won't save. :S

This is starting to bug me, I really want to use Scite. :(

---

### Post by Brenlae on 2006-10-19
I found out the problem.

...

I was saving in /home/ and not /home/brenlae...

Sorry for the waste of time :s

---

### Post by dagnabit dang doohickey on 2006-10-19
In the SciTE save window, make sure you're saving to /home/user_name and not to the /home directory. ;)

---

