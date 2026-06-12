---
title: "SCREEN (the comand) issues"
date: 2007-12-08
forum: General Help
---

### Post by Sjovan on 2007-12-08
Okay... I'm remote at the time and some wierd stuff is going on...

Earlier when I used the comand screen -r i got a list of all the screens, then I put in like screen -r and the first two digets and the screen apeard.
Now it doesn't work that way any more. When i type screen -r a screen popps up (and i'm running like 4 screens at the moment).

```
sjovan@analplugg:~$ screen -list
There is a screen on:
        23875.pts-0.analplugg   (Attached)
1 Socket in /var/run/screen/S-sjovan.
```

```
sjovan@analplugg:~$ ps aux | grep SCREEN
sjovan     758  0.0  0.0   2972   748 pts/6    R+   04:38   0:00 grep SCREEN
sjovan   23875  0.0  0.3   6268  3420 ?        Ss   Dec06   0:09 SCREEN finch

```

As you can se not even the ps comand findes more then one screen, but when i'm a screen C-a n works fine and i have no problem jumping between the fore screens. Any ide why it's acting this way?

---

### Post by Sjovan on 2007-12-09
didn't say anything about bumping in the FAQ, so... 

*bump*

post was on the 2. page.

pleas PM me if this is not allowed.

---

### Post by Sjovan on 2007-12-10
*bump*

---

### Post by mali2297 on 2007-12-10
> **Sjovan said:**
> 
As you can se not even the ps comand findes more then one screen, but when i'm a screen C-a n works fine and i have no problem jumping between the fore screens. Any ide why it's acting this way?

My guess is that you have four windows within one session, note that *windows* are not the same as *sessions*.

---

