---
title: "Please help! Ubuntu won't boot"
date: 2018-01-24
forum: General Help
---

### Post by lokithefly on 2018-01-24
I just updated Ubuntu 16.04, and now there is a boot issue. After I login, the screen shows the desktop icons and turns black, repeating this. I booted -98 kernel.

I can boot into safe mode with networking and root console...

---

### Post by Bashing-om on 2018-01-24
lokithefly; Hello -

Let's look at this as a broken graphic's driver.

Boot to the login screen, here key combo ctl+alt+F1 to gain a console interface,
Log in here with user name and password .
Now, in this interface what results from terminal command:
```

sudo lshw -C display

```

[INDENT]maybe yes
[INDENT][INDENT]could be not so yes
[/INDENT][/INDENT][/INDENT]

---

