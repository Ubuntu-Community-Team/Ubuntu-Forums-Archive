---
title: "Startup help"
date: 2007-09-12
forum: General Help
---

### Post by foxmulder881 on 2007-09-12
I have been experiencing a weird problem the last couple of days and I have no idea what has caused it and/or how to fix it.


Upon startup of my Ubuntu system, the system itself boots fine. But when my desktop appears, Evolution also opens automatically. It's weird... how do I stop it from doing it?

---

### Post by aot2002 on 2007-09-12
check startup script first

ls /etc/init.d/

if you see evolution script in there 
or 
check here

RUN THIS AT COMMAND LINE
grep -i *evolution* /etc/rc*

also download this
sudo apt-get install bum

and then at command run 
bum
now uncheck evolution if its enable to start on boot


also go here
Go to System > Preferences > Sessions
Select the "Startup Programs" tab

See if its in the startup programs tab

---

### Post by foxmulder881 on 2007-09-12
Thanks very much for your suggestions.
I've tried everything that you suggested but I can't find any trace of Evolution being in the startup programs...


[[IMG]http://img529.imageshack.us/img529/629/screenshotrg1.th.png[/IMG]](http://img529.imageshack.us/my.php?image=screenshotrg1.png)

---

### Post by sisco311 on 2007-09-12
try to delete ~/.gnome2/session file
```
rm ~/.gnome2/session
```

---

### Post by foxmulder881 on 2007-09-12
> **sisco311 said:**
> try to delete ~/.gnome2/session file
```
rm ~/.gnome2/session
```

That worked. Thanks heaps.

---

