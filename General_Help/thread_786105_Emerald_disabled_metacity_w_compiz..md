---
title: "Emerald disabled metacity w/ compiz."
date: 2008-05-07
forum: General Help
---

### Post by patrickaupperle on 2008-05-07
I installed Emerald and did ```
emerald --replace
``` and everything worked great. Then I tried to go back. I typed ```
metacity --replace
``` (spelled correctly if that was not). It went back to the metacity theme. Only problem was there was no compiz. I then did```
compiz --replace
``` and it went back to emerald. Can anyone help?

---

### Post by Rocket2DMn on 2008-05-07
Metacity is the basic window manager that comes with Ubuntu.  Compiz is it's own window manager, and I believe Emerald is a window decorator for Compiz.  So, Compiz and Emerald work together, but Metacity is different (no desktop effects).

---

### Post by patrickaupperle on 2008-05-07
I had desktop effects before I got emerald. Can I go back? Should I reinstall Ubuntu?
The above method worked back in 7.10.

---

### Post by FuturePilot on 2008-05-07
There's two ways to fix this.

1. Uninstall Emerald
```
sudo apt-get remove emerald
```
and restart Compiz

--OR--

2. 
```
mkdir -p ~/.config/compiz/ && echo USE_EMERALD=no >> ~/.config/compiz/compiz-manager
```
and restart Compiz

---

### Post by patrickaupperle on 2008-05-07
> **FuturePilot said:**
> There's two ways to fix this.

1. Uninstall Emerald
```
sudo apt-get remove emerald
```
and restart Compiz

--OR--

2. 
```
mkdir -p ~/.config/compiz/ && echo USE_EMERALD=no >> ~/.config/compiz/compiz-manager
```
and restart Compiz

Thank you. :guitar:  That rocks. One question, though, If I remove Emerald and then add it back later, will I keep my themes?

---

### Post by FuturePilot on 2008-05-07
> **patrickaupperle said:**
> Thank you. :guitar:  That rocks. One question, though, If I remove Emerald and then add it back later, will I keep my themes?

You're welcome :)
Yes, your themes will still be there.

---

### Post by patrickaupperle on 2008-05-07
:guitar::guitar::guitar:
Thank you. This is extremely helpful.

---

### Post by SomeGuyDude on 2008-05-08
A much, much easier method in case you want to be able to use Emerald sometimes as well as Metacity.

After you do:

```
emerald --replace
```

You can do:

```
metacity --replace
```

This WILL kill compiz. But wait. Now do:

```
killall emerald
```

Now put in:

```
compiz --replace
```

And you should have compiz going with Metacity window borders. Easy pie.

---

### Post by patrickaupperle on 2008-05-08
> **SomeGuyDude said:**
> A much, much easier method in case you want to be able to use Emerald sometimes as well as Metacity.

After you do:

```
emerald --replace
```

You can do:

```
metacity --replace
```

This WILL kill compiz. But wait. Now do:

```
killall emerald
```

Now put in:

```
compiz --replace
```

And you should have compiz going with Metacity window borders. Easy pie.

After that can I do emerald --replace and get emerald back?

Edit: I tried it, It does work to do emerald --replace. So thank you. Now I can use either with ease.

---

### Post by aroch1 on 2008-05-16
If you want to switch easily back and forth between emerald and metacity, tryin using fusion-icon!

---

### Post by patrickaupperle on 2008-05-16
> **aroch1 said:**
> If you want to switch easily back and forth between emerald and metacity, tryin using fusion-icon!

I would, but I just put little quick launch icons up there on the top bar.  One for emerald, one for metacity, one to killall emerald, and one for compiz. It makes switching real easy. I might try the icon though anyway.

---

