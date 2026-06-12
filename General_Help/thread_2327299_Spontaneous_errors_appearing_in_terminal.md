---
title: "Spontaneous errors appearing in terminal"
date: 2016-06-09
forum: General Help
---

### Post by scottbomb on 2016-06-09
I'm connected to a machine via SSH. Suddenly, it starts displaying these errors all on it's own with no input from me, a phenomenon I've never seen before. Sure, I've typed incorrect commands and gotten errors before but I've never had an error appear in a terminal window when it's just sitting there and I've done nothing. 

How does this happen?

FWIW, the error goes something like this:

```
scottbomb@main:~$ WARNING:tornado.access:404 HEAD /blocks/...a long string of letters and numbers...
```

This error repeats about 10 times and stops. It keeps referring to an IP address that doesn't even exist on our network (192.198.1.176).

---

