---
title: "Emerald crash?"
date: 2008-01-13
forum: General Help
---

### Post by ckamc on 2008-01-13
I currently use this application but I am not sure if its the source of the problem.

If this is a system bug I would like to help contribute (even tho new) into getting it fixed or filed as a bug.

[B]How it happens

[/B]When I do alt+tab and have just one window out on display, and do it more than twice, I lose task bar on the top of every existing application and new application launched (if its not the task bar then its the bar that allows you to close a application window or maximize it... ect)

**What I tried/theories**

I looked thru the running process's to see if its possible to restart it, but do not see it having its own process, thus leaves me the only choice of logging out, then logging back in, in order for me to get things back to normal.

I have not modified the alt+tab portion in compiz... so I don't think it would go inline with that... or does it?

---

### Post by lian1238 on 2008-01-13
To restart emerald, do this.
```
emerald --replace
```
Try using gtk:
```
gtk-window-decorator --replace
```
See if you can reproduce the problem.

---

### Post by perlluver on 2008-01-13
I reproduced it.  With emerald on, Alt+Tab twice, the window decoration disappears.  Can't Alt+F2 to open the run terminal to type in the commands either.

---

### Post by lian1238 on 2008-01-13
What I meant was, can you reproduce it without emerald? Does it happen with gtk?
It is a good idea to put a 'run' button on your panel. This thing happens to me too, but not Alt+Tabbing 2 times. For me, it is random.
Now I have two buttons on my panel, each being a custom application launcher to the following:
```
gtk-window-decorator --replace
```and
```
emerald --replace
```

---

### Post by iyiguncevik on 2008-01-17
I have the same problem. Emerald is keeps crashing all the time, cannot find the reason. That started to happen when I upgraded to Hardy. After upgrading I didn't change any settings no where. There must be smth wrong with Hardy. Any ideas?

---

### Post by Black16V on 2008-02-10
Someone of u reported this bug?

---

