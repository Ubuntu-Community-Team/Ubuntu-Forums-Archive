---
title: "[SOLVED] Main title bar"
date: 2008-05-11
forum: General Help
---

### Post by gwu777 on 2008-05-11
Hi there, I have been playing with compiz-fusion and it crashed at some point - I guess I played too much! Several things have disapeared and I managed to get the option back the way I wanted, however now I do not have anymore the main title bar in all my opened program. The one where there is the minimise, maximise and close icon, this is a slight problem as I have to right click all the time to do the above action or move the window! Anyone can tell me what is wrong? Thank you very much.

---

### Post by aroch1 on 2008-05-16
Hit Alt+F2 and type metactiy --replace, this should cause metacity to take over as your window decorator and give you back what you want.

---

### Post by gwu777 on 2008-05-24
> **aroch1 said:**
> Hit Alt+F2 and type metactiy --replace, this should cause metacity to take over as your window decorator and give you back what you want.

Thank you for this, I have type metacity --replace, and the title bar did come back, but all my desktop effect have gone, I have re-enabled them and now the title bar is gone again on all my windows, I do not have the close, minimise and enlarge buttons. I think it has something to do with compiz as it happens only when I enable the desktop effect.

If you have more idea!!!

Just to had, when I hit alt+F2 the command prompt doesn't show up when the effects are enabled, if that is linked???

---

### Post by rajaram_s on 2008-05-24
This might be because ur graphics driver is blacklisted... were the desktop effects working before you were playing around with it?

---

### Post by gwu777 on 2008-05-24
> **rajaram_s said:**
> This might be because ur graphics driver is blacklisted... were the desktop effects working before you were playing around with it?

Yes they were... I have found the solution, it was quite simple and stupid, in compiz setting manager, if you disable the effect: Windows decoration, you lose the main title bar, which I did! I have now re-enabled it and everything is back to normal. I have been looking for days and I am glad I have found a very simple explanation as to why it didn't work.

The good things is while searching I have discovered emerald and I think I am going to like it!

---

### Post by Amzer zo on 2008-11-23
I have the same problem on kubuntu 8.10, I can't disable compiz it appears and the main title bars are gone.

How to the recover the original settings? (given that the graphical tools don't seem to be willing to cooperate)

---

### Post by Amzer zo on 2008-11-24
Executing the command "kwin --replace" in a konsole (still within KDE) restored my settings (after logout and back into KDE)...

---

### Post by eternalnewbee on 2008-11-24
> Yes they were... I have found the solution, it was quite simple and stupid, in compiz setting manager, if you disable the effect: Windows decoration, you lose the main title bar, which I did! I have now re-enabled it and everything is back to normal. I have been looking for days and I am glad I have found a very simple explanation as to why it didn't work.

The good things is while searching I have discovered emerald and I think I am going to like it!
Every time an issue is solved, go to thread Tools (at the top of this page) to mark the thread as solved. That's how we like it here. Glad your issue is solved **gwu777**.
May the Ubuntu Force be with you.

---

