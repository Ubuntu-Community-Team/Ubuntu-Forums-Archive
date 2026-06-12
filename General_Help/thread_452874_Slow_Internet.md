---
title: "Slow Internet"
date: 2007-05-23
forum: General Help
---

### Post by fmz on 2007-05-23
Hey all, I just installed Linux Ubuntu and upgraded to 7.04 version, but i have one problem my internet is very slow, specially when im lookin on googles, or switchin to other website, on windows xp its fast and normal. Im using DSL RUTER (2wire 1800hg) any ideas why?

---

### Post by DjBeck on 2007-05-23
> **fmz said:**
> Hey all, I just installed Linux Ubuntu and upgraded to 7.04 version, but i have one problem my internet is very slow, specially when im lookin on googles, or switchin to other website, on windows xp its fast and normal. Im using DSL RUTER (2wire 1800hg) any ideas why?

I guess you're using Firefox?
Open a new tab, and go to about:config. Change the following values:
```

network.dns.disableIPv6 -> true
network.http.pipelining -> true
network.http.pipelining.maxrequests -> 8
network.http.proxy.pipelining -> true

```

Restart the browser. Hopefully this'll speed things up for you. Otherwise, there's a plugin called Fasterfox that might help.
[http://fasterfox.mozdev.org/](http://fasterfox.mozdev.org/)

---

### Post by fmz on 2007-05-23
Wow, thanks a lot bro, its faster now ;)

---

