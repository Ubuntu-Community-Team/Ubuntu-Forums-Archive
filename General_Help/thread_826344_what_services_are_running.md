---
title: "what services are running?"
date: 2008-06-11
forum: General Help
---

### Post by zombrax on 2008-06-11
Hey guys,

Just a quick question for all ya gurus..

what command can i use to see what services are running and what command is used for starting and stopping services?

many thanks.

---

### Post by sdennie on 2008-06-11
Going to System->Administration->Services will give you a list of common services that are running that are possible to turn on/off.  I don't know how to get a complete list of "services" though (using top in a terminal may give you a better of idea of what is running).  However many things can be turned on/off/reset using scripts in /etc/init.d.  For example:

```

sudo /etc/init.d/some_service start
sudo /etc/init.d/some_service stop
sudo /etc/init.d/some_service restart

```

---

### Post by iaculallad on 2008-06-11
> **zombrax said:**
> Hey guys,

Just a quick question for all ya gurus..

what command can i use to see what services are running and what command is used for starting and stopping services?

many thanks.

You can use (top) to view what services are running in your system realtime.

```
top
```

---

### Post by zombrax on 2008-06-14
many thanks fellas :)

---

### Post by kerry_s on 2008-06-14
you can also use "pstree" in term.

---

