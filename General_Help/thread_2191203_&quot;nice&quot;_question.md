---
title: "&quot;nice&quot; question"
date: 2013-12-01
forum: General Help
---

### Post by wes.murrell on 2013-12-01
So I am running a CS:GO server on ubuntu desktop 12.04 LTS (I uninstalled the gui package) and i want to use the nice command to change the process of my server after starting it up. I can't launch the server with nice because I don't want to launch the server in root because that could lead to some bad things.

So far i have come up  with ```
renice -n -10 -p "pidof srcds_linux"
``` but for some reason it always returns me with something saying ```
renice: bad value pidof srcds_linux
```

I know that there is probably a really simple and obvious fix, but I am not always the most observant person, could someone please help me?

---

### Post by wes.murrell on 2013-12-01
Nevermind, I have figured it out. I need to use ` instead of "

---

### Post by Lars Noodén on 2013-12-01
It's often even better to wrap it in $()

```

renice -n -10 -p $(pidof srcds_linux)

```

$(..) is usually [preferred over backticks](http://mywiki.wooledge.org/BashFAQ/082).  It's more readable and can be nested.

Also it is possible to launch a process using nice even if you aren't root, just not to raise the priority.

---

