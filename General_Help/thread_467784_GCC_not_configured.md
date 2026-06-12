---
title: "GCC not configured?"
date: 2007-06-08
forum: General Help
---

### Post by Jungle-Cat on 2007-06-08
Im fairly new to ubuntu, and linux for that matter. So please bare with me.

Ive gotten 2 apps in my possesion, which are in tar.gz format. Now from my small experience i do know what to do with them.

Extract, then cd into them and "./configure" which will use gcc to do something, then i can "make" the app.

However, check this out.
[http://img172.imageshack.us/img172/6946/gccwk8.png](http://img172.imageshack.us/img172/6946/gccwk8.png)

Does this mean i have to configure gcc to make executable files?
Also, ive had this problem with something else before, but neglected it. Im really wanting to get it work now.

thanks

---

### Post by mills on 2007-06-08
have you installed gcc?

```
sudo aptitude install build-essential
```

---

### Post by Jungle-Cat on 2007-06-08
after installing buid-essential, configure runs, but "make" or "make install" fail to work. It appears to be undeifened, but the apps readme says thats how to isntall

---

### Post by mills on 2007-06-08
as far as i can tell grubconf has been [abandoned]("http://ubuntuforums.org/showthread.php?t=339776&highlight=grubconf"), its a few years old now so maybe it doesnt work in the new kernel or something. 

there are plenty of other grub editors out there, what about GrubED?

---

