---
title: "[SOLVED] Ubuntu 6.10 does not shut down!"
date: 2007-04-04
forum: General Help
---

### Post by HighD on 2007-04-04
Ok, so I got this  - Intel Celeron@1.2ghz / 128Mb Ram / Matsonic MS7308E Mobo - computer setup as a server (Ubuntu 6.10 Server that is...), no graphic libraries by the way. The problem is it does not seem to shutdown. Whenever I do:

```
shutdown -h now
```

it responds: 

> The system is going down for halt NOW!

[ 581.002161] System halted.

Any idea on what it could be? I'm really lost here :-k 

Well thanks in advance for any help ;-)

---

### Post by confused57 on 2007-04-04
Maybe this will help:
[http://ubuntuforums.org/showpost.php?p=1714220&postcount=9](http://ubuntuforums.org/showpost.php?p=1714220&postcount=9)

except you'll need to use "sudo nano...."  instead of "sudo gedit..."

---

### Post by HighD on 2007-04-04
> **confused57 said:**
> Maybe this will help:
[http://ubuntuforums.org/showpost.php?p=1714220&postcount=9](http://ubuntuforums.org/showpost.php?p=1714220&postcount=9)

except you'll need to use "sudo nano...."  instead of "sudo gedit..."

AWESOME!! It shuts down perfectly now!! Thanks for the tip confused57! :biggrin:

---

