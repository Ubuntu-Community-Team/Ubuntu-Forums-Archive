---
title: "[SOLVED] Can't Roll-up with mouse wheel"
date: 2008-05-20
forum: General Help
---

### Post by castironpants on 2008-05-20
I like being able to activate the Shade (or Roll-Up) via the mouse wheel over titlebars. I'm using compiz and metacity, and the effect is an option in Ubuntu Tweak. It used to work for me, but now when I set it and close Ubuntu Tweak, nothing happens, and when I load it again the option is unset. It works with emerald themes, but how can I get my metacity roll-up back?

---

### Post by Forlong on 2008-05-20
```
gconftool-2 -s -t string /apps/gwd/mouse_wheel_action shade
```

---

### Post by castironpants on 2008-05-20
Yep, that did it! Thanks!

---

### Post by Exsecrabilus on 2008-05-20
Did you download the new Ubuntu Tweak v0.3.1 for Hardy?

If not, go [here](http://ubuntu-tweak.com/downloads) and download it!

---

### Post by castironpants on 2008-05-20
Yeah, the most recent one.

---

