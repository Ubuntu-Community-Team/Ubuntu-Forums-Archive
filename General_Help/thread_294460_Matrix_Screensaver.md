---
title: "Matrix Screensaver"
date: 2006-11-06
forum: General Help
---

### Post by Sethro on 2006-11-06
Hi everyone,

I just downgraded from Ubuntu 6.10 to 6.06 and I loved the really cool matrix screensaver that Ubuntu 6.10 had. In 6.06 I get a matrix screensaver but it sucks and only shows pictures of Matrix Charecter, I just want the one with the code falling down.

How can I install the new one on 6.10???

---

### Post by po0f on 2006-11-06
Sethro,

Try installing xscreensaver-gl and/or xscreensaver-gl-extra.
```
$ sudo aptitude install xscreensaver-gl xscreensaver-gl-extra
```

---

### Post by Sethro on 2006-11-07
Yeah I was able to get a whole bunch of more screensavers but not the cool matrix one?

---

### Post by Choad on 2006-11-07
its called GL matrix... so u got to look at the "G" section not the "M" section ;)

---

### Post by CatKiller on 2006-11-07
The one that it **just** the code falling down is called XMatrix and is included in the **xscreensaver-data-extra** package.

The one that's code falling down that has depth is called GLMatrix and is included in the **xscreensaver-gl** package.

---

### Post by Sethro on 2006-11-07
> **CatKiller said:**
> The one that it **just** the code falling down is called XMatrix and is included in the **xscreensaver-data-extra** package.

The one that's code falling down that has depth is called GLMatrix and is included in the **xscreensaver-gl** package.

Yup, thanks that did it. Got the cool matrix screensaver goin...

---

### Post by fa6ista on 2007-09-28
> **Sethro said:**
> Yup, thanks that did it. Got the cool matrix screensaver goin...

Not me.... I installed all the packages mentioned above, and still
don't have the falling code screensaver.... what  am I missing?

---

### Post by virtudtierra on 2007-11-10
> **fa6ista said:**
> Not me.... I installed all the packages mentioned above, and still
don't have the falling code screensaver.... what  am I missing?

you must run it at konsole or Terminal: you must write 

$ xscreensaver 

and it'll runs.):P

enjoy it;)

---

