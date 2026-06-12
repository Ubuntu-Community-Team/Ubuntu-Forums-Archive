---
title: "how to install/use CGWD themes?"
date: 2008-06-23
forum: General Help
---

### Post by karasuman on 2008-06-23
I've looked around for help with this, but I'm not coming up with much.  There are some themes on gnome.look that I really like, and they all end with .cgwdtheme.  I can't figure out how to install these.  I tried

```
sudo apt-get install cgwd
```

but it sounds like cgwd somehow became part of emerald...or something?  I already had emerald installed when I first tried this.  I used the synaptic package manager to remove emerald, and THEN did the above command again...and it reinstalled emerald.  I'm a bit confused.

What do I do with a file that ends in .cgwdtheme?  Emerald can't seem to import these, and neither does the default theme manager recognize them as themes.

---

### Post by isaacj87 on 2008-06-23
Hey there,

Emerald can handle these files. Just rename the files to .emerald and you should be able to import them. For example, "sparkly.cgwdtheme" to "sparkly.emerald"

IIRC, "Custom-Generic-Window-Decorator" got phased out and all work was re-directed to Emerald. According to the Beryl wikipedia page:

> 
The window decorator, formerly known as cgwd, was renamed emerald. A cgwd theme could be ported to emerald by changing the extension from .cgwd to .emerald.

Some more info:

> Emerald, the default window decorator and a continuation of cgwd, had its own theme format and supported effects like alpha transparency, a fork of Compiz's gtk-window-decorator.

To be honest, it's a little strange that an author on Gnome-look.org is still putting out a CGWD version as CGWD has not been used for quite some time. Hope that works for you!

-Isaac

---

### Post by karasuman on 2008-06-23
Thank you very much!

---

