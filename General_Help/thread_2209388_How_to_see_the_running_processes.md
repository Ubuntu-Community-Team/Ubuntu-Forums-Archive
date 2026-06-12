---
title: "How to see the running processes?"
date: 2014-03-05
forum: General Help
---

### Post by goghvv on 2014-03-05
Hi, I'm running Linux ubuntu 3.11.0-15, and I want to see all the currently running processes.
I ran the command ps to terminal, and only got:
```
  PID TTY          TIME CMD
 3048 pts/1    00:00:00 bash
 3590 pts/1    00:00:00 ps

```
where in fact, I have "Eclipse", "Document viewer", and "Mozilla Firefox" open, and none of it is in that list.
What am I missing?

Thanks in advanced!

---

### Post by mikewhatever on 2014-03-05
Try **ps ax** instead.

---

### Post by tgalati4 on 2014-03-05
```
ps -ef
ps aux
ps aux | grep firefox
ps aux | more
top
sudo apt-get install htop
htop
```

ps only shows what is in the current user shell--which is not much--*bash* and *ps*!

---

### Post by goghvv on 2014-03-05
Great. thank you both.

---

### Post by amish_otaku on 2014-03-05
Why not use top or htop? They will give you a comple listing of all process running on the current machine.

---

