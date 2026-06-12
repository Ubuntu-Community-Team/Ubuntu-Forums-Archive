---
title: "Enabled Compiz Fusion..."
date: 2007-09-25
forum: General Help
---

### Post by Belinrahs on 2007-09-25
and my screen goes entirely white.

I installed the correct packages, configured them, etc, etc. But when I enable them, the screen starts flickering, windows are still there but the top and bottom bars disappear. Then the screen goes entirely white. My cursor is still there and perfectly smooth. Windows are still evidently there because if I get my cursor in a certain place then drag it seems to be dragging a window.

So I unplugged my computer and restarted it. It seemed to start OK, it got to the login screen, I type in my credentials and it seems to login just fine. Nautilus loads, everything in the little Ubuntu loading window. Then Compiz seems to take over and it goes completely white again, with my cursor completely usable and smooth.

I can't turn off compiz now, I just want it gone. I still have my feisty CD but I'd rather not reinstall. I had important stuff on here.

I am comfortable using Terminal if I need to, so if it involves that just tell me what to type :)

Thanks

---

### Post by xmouse on 2007-09-25
Just tipe in:
```
gnome-xgl-switch --disable-xgl
```
I think it'll work

---

### Post by RebounD11 on 2007-09-25
I had that same problem before, but it "magically" went away... anyway I can help U turn off CF.

If your cursor is moving and it behaves normally (dragging windows and such) it means X server is still running underneath that whiteness, U just can't see it. So all U have to do is press Alt+F2 and type :

metacity --replace

and if U typed it wright the whiteness will disappear.

Hope it helps!

---

### Post by Belinrahs on 2007-10-03
> **RebounD11 said:**
> I had that same problem before, but it "magically" went away... anyway I can help U turn off CF.

If your cursor is moving and it behaves normally (dragging windows and such) it means X server is still running underneath that whiteness, U just can't see it. So all U have to do is press Alt+F2 and type :

metacity --replace

and if U typed it wright the whiteness will disappear.

Hope it helps!
metacity --replace worked.

Thanks for the help.

---

