---
title: "slrn and line drawing"
date: 2005-06-03
forum: General Help
---

### Post by mightymartianca on 2005-06-03
I having a small problem with slrn and line drawing.  Instead of nice lines for the thread trees, I'm getting not-so-nice "mq" characters.  One source seems to indicate that it might be terminfo.  It's happening from a xterm window and from PuTTY on my Windows box.  Any hints would be greatly appreciated.

---

### Post by garlito on 2005-06-03
Is your locale utf-8 ? Slrn doesn't work with this codification yet. I think that it will be done in the next version

You might try put in the config file:

set simulate_graphic_chars 1

But it's possible that neither works in a utf-8 terminal

Bye

---

### Post by djrosen on 2005-08-21
Try setting the locale to en_US.ISO8859-1 (or just en_US).  You may need
to generate the additional locales by running:

```
$ sudo dpkg-reconfigure locales
```

then set the environment variables:

```
export LANG='en_US.ISO-8859-1'
export LC_CTYPE='en_US.ISO-8859-1
```

in your choice of files, I put it in 

~/.bashrc

I had the exact same problem and this worked for me.

-- 
David

---

