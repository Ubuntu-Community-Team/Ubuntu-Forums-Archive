---
title: "Can't click on desktop"
date: 2014-07-13
forum: General Help
---

### Post by jamessmithgator on 2014-07-13
I have two monitors and for some reason I can't click on any windows or Icons on one of them but I can click on the taskbar, and my other screen is unaffected.

---

### Post by slooksterpsv on 2014-07-13
What kind of system, what kind of graphics cards, what version of Ubuntu (12.04, 14.04, 13.10, etc.); 32-bit or 64-bit. If you can give us some of that information we may be able to help.

---

### Post by jamessmithgator on 2014-07-14
it generally happens after closing a game (i.e world of tanks) 
I am running:
Ubuntu 14.04 64bit
Nvidia GTX 550 ti
8GB RAM
Intel® Core&#8482; i7-3820 CPU @ 3.60GHz × 8

---

### Post by slooksterpsv on 2014-07-14
That makes sense if it's happening after closing a game. My personal experience with this one is even though you've closed the game, the process is still running in the background. I haven't had this issue since 10.04, but it looks like it still happens. If you run:
```

ps aux | grep *name_of_games_executable*

```

E.g.
ps aux | grep chrome

You should be able to kill it via:
kill *process_number*

Lets say it was 2458 you'd do
kill 2458

---

