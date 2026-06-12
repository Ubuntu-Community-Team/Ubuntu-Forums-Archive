---
title: "Unable to update software"
date: 2007-10-14
forum: General Help
---

### Post by DalekClock on 2007-10-14
I'm trying to update a certain package. When I click "Install Updates", I get the following error:```
E: dpkg was interrupted, you must manually run 'dpkg --configire -a' to fix this problem.
E: _cache->open() failed, please report.
```I've tried the command suggested, but was unsuccessful. Has the cache error got anything to do with this?

---

### Post by wormser on 2007-10-14
Did you put sudo before the command?

```
sudo dpkg --configire -a
```

---

### Post by frankjguti on 2007-10-21
I have the same problem.  I did and then it asked me for a password which it did not let me even type.  And besides not being able to get my upgdates.  I have not been able to download any software.  Then I tried to boot from my cd rom and I couldnt,  I dont know if that has anything to do with it.  I also want to install windows if it lets me.

---

### Post by FuturePilot on 2007-10-21
When it asks for your password just type it in. You won't see anything. It's just an inconsistency between the GUI and the terminal. You can read more about it here
[http://www.psychocats.net/ubuntu/passwordinterminal]("http://www.psychocats.net/ubuntu/passwordinterminal")

---

