---
title: "Cannot set PKG_CONFIG_PATH"
date: 2015-08-09
forum: General Help
---

### Post by ubu88 on 2015-08-09
If I set $PKG_CONFIG_PATH its value will only remain for the lifetime of the terminal. If I open a new terminal its value will be null.

```
export PKG_CONFIG_PATH=/usr/lib/pkgconfig
```

What am I doing wrong?

---

### Post by TheFu on 2015-08-09
Set it somewhere that gets run before the GUI part of your login starts.  ~/.login is the normal place, methinks.  I haven't looked this stuff up - if you google for Linux login steps, it should explain which files are referenced with an order.  There are 5 common files to put stuff like this into.

---

### Post by ubu88 on 2015-08-10
Thanks!

I set it in the [FONT=Helvetica Neue] [/FONT]~/.bashrc file.

---

