---
title: "init.d/rc: not found"
date: 2007-05-10
forum: General Help
---

### Post by drect0r on 2007-05-10
Hello all!
This is my first post, and I first want to thank everyone who has made this distribution possible.  It's really a stellar experience, which is why I'm so bummed about being locked out of my Ubuntu now!

So, I messed with the /etc/init.d/rc file in a misguided attempt to add better power management (should have put a new script in that folder, right?  not mucked with that file.. oh well
When the system didnt start up I went into XP and used the ext3 driver I have to edit the file back, but this driver doesnt deal well with permissions so now I have the error:

exec: 8: /etc/init.d/rc: not found
init: rcS main process (2368) terminated with status 2

I tried booting into a liveCD and changing the permissions to everything I could think of - it is already owned by root.  Any suggestions?
Thanks!

---

### Post by zvacet on 2007-05-10
```
sudo gedit /etc/init.d/rc
```

And if you know what did you change back to default

---

### Post by drect0r on 2007-05-10
thanks for the quick reply!
It already is back to default, the same file it was before.  Also, I cant do thinks like gedit since I can only boot into a command prompt in the livecd I have

---

