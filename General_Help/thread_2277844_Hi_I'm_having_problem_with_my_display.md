---
title: "Hi I'm having problem with my display"
date: 2015-05-11
forum: General Help
---

### Post by andreadixon825 on 2015-05-11
Hi, I don't know what I did but I'm not getting full screen on my monitors the edges are black and the gui screen small. I have two wide screen monitors and it worked good but then It stopped. Now showing on one screen and not the other. I have looked though Synaptic package manger but not sure what I'm looking for. Please help Thank you :)

---

### Post by tgalati4 on 2015-05-11
Open a terminal and page through your log file.  Look for errors.

```
less /var/log/Xorg.0.log
```

Spacebar to page forward, "q" to quit.

---

### Post by andreadixon825 on 2015-05-11
Hi' Im geting a error when typing in less /ver/log/xorg.0.log
less /ver/log/xorg.0.log: No such file or directory

What do I do know?

---

### Post by tgalati4 on 2015-05-11
Spell *var* correctly.  And Xorg not xorg.

Try this command:

```
grep EE /var/log/Xorg.0.log
```

---

### Post by andreadixon825 on 2015-05-12
Hi this is what I get. And sorry about that sometimes I type to fast :)
> 
(II) Loading extension MIT-SCREEN_SAVER
(EE) faild to load module "nvidia"  (module does not exit, 0)
(EE) faild to load module "nv"  (module does not exit, 0)
(EE) faild to load module "nvidia"  (module does not exit, 0)
(EE) faild to load module "nv"  (module does not exit, 0)


---

