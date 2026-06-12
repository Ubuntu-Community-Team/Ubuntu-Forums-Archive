---
title: "Keyboard swap keys"
date: 2008-06-05
forum: General Help
---

### Post by thursty on 2008-06-05
Hi,

Having spilled drink all over my laptop (for the second time!) the only thing wrong is that the 'a' key doesn't work.

Is it possible for me to set the 'Function' or 'Windows' key (which are nearby) to now work as the 'a'?

Cheers.

---

### Post by drs305 on 2008-06-05
You can try *xmodmap*.

Start by running *xev*.
```
xev
```

It will open a small window. You will see in terminal the code of any key you press. Of course, if 'a' doesn't work, you may have a problem. On my machine the 'a' key is # 38, and "*a*". The left windows key on my keyboard is # 115, "Super_L"

 The command would be:
```
xmodmap -e "keysym Super_L = a"
```

If that works, you can put it as a command in Sessions (System, Preferences, Session) to run at startup.

---

