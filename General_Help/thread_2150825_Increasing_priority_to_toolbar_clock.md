---
title: "Increasing priority to toolbar clock?"
date: 2013-06-02
forum: General Help
---

### Post by Rocket J Squirrel on 2013-06-02
Running Lubuntu 12.04 in a radio broadcast environment where I need to keep close watch on the time down to the second. 

I notice that the toolbar clock will sometimes stop counting seconds while another process loads or runs. Then it catches up but this may take 10 seconds or more. Is there a way to increase the priority of the clock to help it stay current?

---

### Post by Rocket J Squirrel on 2013-06-03
Possibly too weird of a question? Surely someone knows how to keep the toolbar clock locked in despite other processes?

---

### Post by tgalati4 on 2013-06-03
```
man nice
man xclock
```

*xclock* used to have a second hand, but I can't find the switch.  You can try to *nice gnome-panel* or whatever the panel/toolbar is called in lubuntu.  If the priority is too high, it might affect the responsiveness of the system, so try small increments.

---

### Post by vasa1 on 2013-06-03
> **Rocket J Squirrel said:**
> Possibly too weird of a question? Surely someone knows how to keep the toolbar clock locked in despite other processes?
I find it a very interesting question!
Could you also give details of your CPU and RAM?
And in Lubuntu, it should be "lxpanel". I don't think the clock is running independently.

---

### Post by HiImTye on 2013-06-04
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
you can try a terminal clock```
sudo apt-get install tty-clock
tty-clock -sc
```

---

