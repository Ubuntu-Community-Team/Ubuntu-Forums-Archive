---
title: "System shut down/log off problems"
date: 2008-04-27
forum: General Help
---

### Post by brett611 on 2008-04-27
I thought this problem was attributable to Hardy upgrade, but I reinstalled Gutsy and the problem remains.  Specifically:

When clicking 'log off', 'restart' or 'turnoff' I get sent to a black screen of death.  Alt-Backspace will eventually kick me to the user log on screen.

Suggestions?
Thanks!

---

### Post by ghost_ryder35 on 2008-04-27
switch to vty next time you want to shutdown and issue
```

halt

```
and see what the errors are and or where it hangs durning this process of shuting down

---

### Post by brett611 on 2008-04-27
whats vty?
thx

---

### Post by QwUo173Hy on 2008-04-27
I think he means a virtual terminal. If you press Control+Alt+F1 you will get virtual terminal 1 and can log in there and try the command. You may need to run it as root (sudo halt).

Let us know how you get on.

---

### Post by brett611 on 2008-04-28
thanks all.

I jumped on the pc this am to start the trouble shooting process and it appears to have fixed itself overnight.  that's a first for me.

thx again

ps - i tried last night logging in via ctrl-alt-F1 and nothing happened - no error messages, just a blinking cursor

marking as solved
(whoops - can't find the 'solved' option in thread tools...?)

---

