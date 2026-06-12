---
title: "Keyboard bug. Enter key doesn't work anymore"
date: 2007-12-31
forum: General Help
---

### Post by silverhammermba on 2007-12-31
My enter key has worked in the past, but I've been messing around in Compiz lately and now it no longer works. I restored defaults in Compiz, but that hasn't fixed the problem. I also searched through my configuration files for some binding that was using enter but nothing is. I know that they key isn't physically broken because when I hit enter the text cursor flashes quickly - which leads me to believe that there is some hidden binding currently occupying it.

---

### Post by silverhammermba on 2007-12-31
I'm still having this problem. I can't use terminal at all because I can't hit enter! Does anyone have any ideas what files I could edit or what settings I could look at to fix this? I'd fix it myself if I could, but I don't know what's causing my problem nor how to find out.

---

### Post by geraldm on 2007-12-31
You can use xev program to check what codes the key is providing.
```

xev

```

Gerald

---

### Post by silverhammermba on 2007-12-31
Ok... weird. I tried that xev thing and was about to paste my output here, but now my enter key works all of a sudden! So I don't know what fixed it but thanks anyway! :)

---

### Post by word327 on 2008-02-09
having the same problem...
ctrl+enter works as just enter used to...
here's xev output when I press enter:
```

FocusIn event, serial 31, synthetic NO, window 0x3000001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0 

```

---

