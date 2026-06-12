---
title: "firefox maximized compiz"
date: 2008-05-09
forum: General Help
---

### Post by kolbycrouch on 2008-05-09
after i installed compiz-fusion git0.75 the gnome panel and window bar dont show up in firefox. take a look at the screenshot. is it ubuntu or the compiz git?

---

### Post by prshah on 2008-05-09
> **kolbycrouch said:**
> after i installed compiz-fusion git0.75 the gnome panel and window bar dont show up in firefox. take a look at the screenshot. is it ubuntu or the compiz git?

Press alt+F2, then give the command ```
compiz --replace
``` and press enter; did the titlebars reappear? If they didn't press Alt+F2 and give the command ```
metacity --replace
```, did they reappear now?

---

### Post by Enigmatic on 2008-05-13
I have the same issue, but neither command worked for me.

---

### Post by mano cazalet on 2008-05-13
it happens here sometimes
but always go back to normal after hitting F11 twice (wait till it goes to fullscreen and hit again to go back to normal)

---

### Post by Znort_Ubern00b on 2008-05-14
If you are using an NVidia card then try this code in terminal...

sudo nvidia-xconfig --add-argb-glx-visuals -d 24


then type in terminal

emerald --replace or metacity --replace (depending on which manager you use).

and then

compiz --replace

---

### Post by Carlbc18 on 2008-06-04
I'm having this problem too, but i'm not using the NVidia card, I have the ATI graphics card on my IBM T-60.  The metacity --replace and the compiz --replace didn't work.  F11 twice only hide the firefox menu (tools, views, etc)

---

### Post by Carlbc18 on 2008-06-05
Anyone?

---

### Post by jpeddicord on 2008-06-05
The most likely cause is that your window manager has crashed. Hit Alt+F1 to bring up the Applications menu, and then Accessories > Terminal. In the terminal window, type the following and then hit Enter:

```
metacity --replace
```

If you get any errors, select them with your mouse, right-click, and Copy. Paste them in here so we can get an idea of what is going wrong.

---

### Post by sloan1919 on 2009-02-06
I can confirm I have the same problem. Pressing F11 twice does correct it but its annoying none the less.

Sloan

---

### Post by abbaseo on 2009-02-08
indeed Sloan, i am with you on this, same problem, no solution and f11 is annoying

---

### Post by not a pipe on 2009-02-08
This has happened to me a few times, but not frequently.

---

### Post by Found on 2009-04-01
having the same problem
i guess the only way to fix it, by pressing f11 every time
....

ok, i found how to fix this one, at least it works for me
if you go to

_System -> Preferences -> CompizConfig Settings Manager -> Workarounds_

and uncheck **Legacy Fullscreen Support** it will works fine.
However, i'm not shure if this option affects any other important features...

---

### Post by plamen_todoroff on 2009-04-02
In typical linux style (jokingly) I would say "It's not a bug, it's a feature."

:shock: 

By the way, on your computer, does this affects only firefox?

---

### Post by Found on 2009-04-22
> **plamen_todoroff said:**
> In typical linux style (jokingly) I would say "It's not a bug, it's a feature."

:shock: 

By the way, on your computer, does this affects only firefox?

well yes, no other windows behave like that
but now it's fine :)

---

