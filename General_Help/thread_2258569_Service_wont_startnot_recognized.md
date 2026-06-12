---
title: "Service wont start/not recognized"
date: 2014-12-28
forum: General Help
---

### Post by mike236 on 2014-12-28
Ubuntu Server 14.04, no gui

I created a startup script and moved it to /etc/init.d/multicraft

I then entered sudo chmod a+x multicraft
Then sudo update-rc.d multicraft defaults

No errors showed.

I restarted the system and the multicraft did not start. When I tried service multicraft start , it told me no such file or directory. Its there for sure and has all the proper permissions, they match all the other services.

Am i missing something to get this fully registered as a startup service.

---

### Post by schragge on 2014-12-28
Does it start with ```
sudo /etc/init.d/multicraft start
```:?:

---

### Post by mike236 on 2014-12-28
nope. Same error, No such file or directory

---

### Post by schragge on 2014-12-29
Then your script is buggy. Try to run it with
```

sudo sh -x /etc/init.d/multicraft start

```
and see at which point it gets aborted.

---

### Post by mike236 on 2014-12-29
dos2unix is now my friend... :rolleyes:

sorry bout that...

works great now

Thanks

---

