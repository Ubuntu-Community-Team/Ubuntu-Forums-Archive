---
title: "Cadsoft eagle with ugly user interface"
date: 2006-12-08
forum: General Help
---

### Post by bgiovanni on 2006-12-08
I use cadsoft eagle and in dapper it work fine but in edgy font and listbox refresh are very crazy

I try some change into .gtkrc and .gtkrc.mine to set font and theme, audacity   work with change but in eagle never change.

Can anyone help me?

---

### Post by d_b on 2007-01-29
Have you found a solution?  I am also having the same problem..  

Best,
d.

---

### Post by linitrofe on 2007-08-27
[https://bugs.launchpad.net/ubuntu/+source/eagle/+bug/110479]("https://bugs.launchpad.net/ubuntu/+source/eagle/+bug/110479")

Use:
```
XLIB_SKIP_ARGB_VISUALS=1 /usr/lib/eagle/bin/eagle
```

---

