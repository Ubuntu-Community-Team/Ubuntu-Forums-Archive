---
title: "How do I install Appache?"
date: 2006-08-08
forum: General Help
---

### Post by webbcm01 on 2006-08-08
I'm very new to the command line.  and compiling programs from source.  I downloaded the appache source and extracted it. i thought i had ran the configuration file just by clicking it and saying run in terminal.  I want to know the command to enter in terminal to configure then what to do from there .  please help.

---

### Post by chaosgeisterchen on 2006-08-08
AFAIK Apache is one of the things running on board of Ubuntu no matter what.

It's started with every boot, at least on my pc, and I never additionally installed it ;)

---

### Post by mlind on 2006-08-08
How about installing it straight from Ubuntu repositories, compiling Apache httpd server from source can be bit tricky..

Type this on terminal
```

sudo aptitude install apache2

```

---

### Post by scxtt on 2006-08-08
[QUOTE=chaosgeisterchen]AFAIK Apache is one of the things running on board of Ubuntu no matter what.

It's started with every boot, at least on my pc, and I never additionally installed it ;)[/QUOTE]i doubt this is the case at all ... it does start @ boot, unless you tell it not to, but i've NEVER seen it installed by default (the server install probably does) ...

---

### Post by chaosgeisterchen on 2006-08-08
Strange, very strange.. I could use localhost php interpreter without additional install I assume. 

Well, could be also different, I do not check all of my updates, but I never explicit gave the order to apt to install apache.

---

### Post by scxtt on 2006-08-08
what does "localhost php interpreter" have to do w/ apache2?  other than the fact that it most likely told you apache would have to be installed also ...

---

### Post by chaosgeisterchen on 2006-08-08
Tell me if I am confusing some things here, as I really become confused myself right now ;)

Is there any alternative to apache to run localhost for things like PHP? An alternative which is onboard installed?

So this could be the thing I used back then and not apache...

---

