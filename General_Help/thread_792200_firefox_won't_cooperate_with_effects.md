---
title: "firefox won't cooperate with effects"
date: 2008-05-12
forum: General Help
---

### Post by justgrant2009 on 2008-05-12
I'm running Hardy and compiz with my graphics card on and "normal" visual effects set, and now when i try and open multiple occurrences of firefox the second one and any there after show up as a window filled black, and no matter what i do there is no way to fix it.  I didn't have this problem before using "no" visual effects.  Any ideas people?

-Grant-

---

### Post by chrisruls00 on 2008-05-12
You are having the black window bug that is caused when too much Texture Memory is used. Firefox uses a lot of texture memory so try to only open one at once. Do you have "Indirect Rendering" and "Loose Binding" set to ON? If you are using fusion-icon they are under options, if not try staring compiz using:

```

Compiz --replace --indirect-rendering --loose-binding

```

---

### Post by justgrant2009 on 2008-05-13
When i try running that code it tells me that everything is fine until it gets to 
"Checking for Xgl: not present";
"/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format";
"GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly."

---

### Post by justgrant2009 on 2008-05-13
Nevermind, i think i got it figured out, I just got compiz fusion working and adjusted the options to on (both that you told me to) and so far so good.  Is this a common problem on other computers too, because i just thought it was because my laptop is pretty old and finicky.

---

