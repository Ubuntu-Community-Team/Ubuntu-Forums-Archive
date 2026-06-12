---
title: "installing a graphics card"
date: 2008-02-05
forum: General Help
---

### Post by gard195 on 2008-02-05
i have a graphics card and i didnt need drivers for windows. (im dual booting)
but when i try to boot ubuntu with card in it wont let me.

---

### Post by Mike'sHardLinux on 2008-02-05
You need to tell us more. What graphics card do you have?

You know, windows needs drivers no matter what graphics card you use. It's just that it comes with a few of them. But, so does Ubuntu.

Also, what do you mean it won't let you? Are you getting a black or white screen? Are you getting an error message? Is it simply freezing completely???

---

### Post by gard195 on 2008-02-06
its a nvidia geforce mx/mx 400.

im getting a black screen asking for password and if i want to diagnose it. but i dont know how to configure it.

---

### Post by pointone on 2008-02-06
If you've changed your graphics card, you'll need to reconfigure X.Org so that it knows what's going on. This can be accomplished by booting into "recovery mode" and running the following command at the prompt:

```
dpkg-reconfigure xserver-xorg -phigh
```

---

### Post by gard195 on 2008-02-07
thank you it worked.

---

### Post by lswest on 2008-02-07
yeah, the problem is it was loading drivers for a card that no longer existed in your PC, always best to change the driver to "vesa" before installing a new card, and then choosing the proper driver after booting up again.  just some advice for next time round ;)

---

### Post by gard195 on 2008-02-07
i chose nv in the options.

---

