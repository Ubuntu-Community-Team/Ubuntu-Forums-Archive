---
title: "Patch command help."
date: 2005-06-28
forum: General Help
---

### Post by afonic on 2005-06-28
Hi there,

does anyone how to use the Linux patch command to patch files in multiple directories?

For example I type:
```
patch -cl -d /home/afonic/program -p1 < newversion.patch
``` 
To get the files inside my program folder updated.

However I want to do it for 100+ users all having the same folder program like this:
/home/username/program/

So the only think that changes is the username. I want to patch ALL users, if possible not one by one!

Thanks for any advice!  :)

---

### Post by adwait on 2005-06-28
umm......dunno abt the proper Linux way to do it, but I would probably just use a c++ program. If the user name are just numbers (like in a college or something) even better (just increment the counter), if not you could get the usr names one by writing the out put of the command "ls /home" and then using each individual name in a for loop.

---

### Post by afonic on 2005-06-29
[QUOTE=adwait]umm......dunno abt the proper Linux way to do it, but I would probably just use a c++ program. If the user name are just numbers (like in a college or something) even better (just increment the counter), if not you could get the usr names one by writing the out put of the command "ls /home" and then using each individual name in a for loop.[/QUOTE]
 Yeah, good call. I was thinking of a shell script too.

I just thought to check out if there was an easy command to do that, thanks.

---

