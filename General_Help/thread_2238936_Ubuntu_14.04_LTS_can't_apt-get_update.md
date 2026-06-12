---
title: "Ubuntu 14.04 LTS can't apt-get update"
date: 2014-08-11
forum: General Help
---

### Post by nona2 on 2014-08-11
Hello Peeps. I've been at it for about 5 hours trying to figure out why when I run a update, it tells me this.

[http://pastebin.com/RafuMfPz](http://pastebin.com/RafuMfPz)

Also, if it's needed here's my sourcelist stuff~ 

[http://pastebin.com/q14pgfRb](http://pastebin.com/q14pgfRb)

I've tried about 4 different services and i still get the same error.


Any help is much appreciated.

Oh yeah, I also tried the sources list generator, that still didn't work for me ;.;

---

### Post by kc1di on 2014-08-11
Hello nona2 and welcome to ubuntu

go to a terminal and try this:

```
sudo rm /var/lib/apt/lists/*
sudo apt-get update
```

if that does not work try changing mirrors.

---

