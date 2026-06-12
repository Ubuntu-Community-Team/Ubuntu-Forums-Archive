---
title: "Login through TTY"
date: 2019-04-04
forum: General Help
---

### Post by meslas on 2019-04-04
How do I login through TTY only and not through any kind of GUIs?

 In detail, i want to:
1. booting my computer
2. tty pops up
3. logging in through tty
4. doing some work
5. if there is a need, starting desktop with startx command

I need this because my computer is old and slow, so logging through tty is much faster.

---

### Post by TheFu on 2019-04-04
You can change the TTY used by pressing <ctl>-<alt>-F1
You can choose the TTY, normally 7 (F7) is the GUI login screen, so picking any other one will get you to a text-only startup. This works. I just tested it again here.

I haven't tried startx in years, so I don't know for certain if it will work without any modification.

---

### Post by meslas on 2019-04-04
> **TheFu said:**
> You can change the TTY used by pressing <ctl>-<alt>-F1
You can choose the TTY, normally 7 (F7) is the GUI login screen, so picking any other one will get you to a text-only startup. This works. I just tested it again here.

I haven't tried startx in years, so I don't know for certain if it will work without any modification.

Yes, it is possible to switch to TTY, but I want by default that my computer booted into TTY and not any graphic login screens.

---

### Post by CatKiller on 2019-04-04
I've never tried it, but I believe it would be ```
sudo systemctl enable multi-user.target
sudo systemctl set-default multi-user.target
```

and to switch back to a graphical login by default would be ```
sudo systemctl set-default graphical.target
```

---

