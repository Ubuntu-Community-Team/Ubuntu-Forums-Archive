---
title: "run script after terminal login"
date: 2008-02-21
forum: General Help
---

### Post by Mr.Johnny on 2008-02-21
Greetings.

I have installed ubuntu server, and then the xfce desktop terminal, but I must type startx everytime I boot and loginl, is there any way of running it automatically after I login in the terminal?

Thanks

---

### Post by mali2297 on 2008-02-21
Add these lines to the end of **~/.profile**:
```

if [ -z "$DISPLAY" ] && [ $(tty) == /dev/tty1 ]; then
  startx
fi

```

EDIT: If you want to run xfce4, you can use **startxfce4** instead of startx.

---

### Post by Mr.Johnny on 2008-02-21
Thanks! :KS

---

