---
title: "Start Emacs other than from terminal"
date: 2007-11-05
forum: General Help
---

### Post by keenlearner on 2007-11-05
Hey, before this I install the emacs terminal one, but then I installed the emacs with its own X-Window, In terminal I can't use the command M-f because it will mean accessing the file menu. is there a way to deal with this ? 

Secondly, when I start emacs from the terminal 
$ emacs

I got the emacs X-window appeared, but I can't use the terminal anymore as it's eaten by the emacs program. When I press CTRL+z to get the terminal back, but the emacs X-window is not more working or accepting my input. is there a way to deal with this ? How come the emacs is not in Applications menu ?

Thank you and Thank you for the two problems.

---

### Post by keenlearner on 2007-11-05
Hi,,,, Anybody has any idea ? Thank you

---

### Post by mali2297 on 2007-11-05
> **keenlearner said:**
> Hey, before this I install the emacs terminal one, but then I installed the emacs with its own X-Window, In terminal I can't use the command M-f because it will mean accessing the file menu. is there a way to deal with this ? 


Strange, for me the problem is opposite. I don't know how to access the pull down menus when Emacs runs in the terminal. M-f moves one word forward.

> 
Secondly, when I start emacs from the terminal 
$ emacs

I got the emacs X-window appeared, but I can't use the terminal anymore as it's eaten by the emacs program. When I press CTRL+z to get the terminal back, but the emacs X-window is not more working or accepting my input. is there a way to deal with this ? 


Start Emacs with
```

emacs &

```
The "&" tells it to run in the background. You can also type **bg** after CTRL+z, that will do the same thing.

An additional alternative is to press ALT+F2, and type emacs into *Run command*.

---

### Post by keenlearner on 2007-11-05
Thanks for the reply, the second problem is solved.
Specifically, the first problem when I press M-f it access the menu of terminal. In contrast, not the menu of emacs, I can't access the emacs menu too.

Thanks.

---

### Post by gaussian on 2007-11-05
> **keenlearner said:**
> Thanks for the reply, the second problem is solved.
Specifically, the first problem when I press M-f it access the menu of terminal. In contrast, not the menu of emacs, I can't access the emacs menu too.

Thanks.

M-` is the keycombination to access menu when running emacs in a terminal.

---

### Post by mali2297 on 2007-11-06
> **gaussian said:**
> M-` is the keycombination to access menu when running emacs in a terminal.

Thanks.

I read the help message at start, apparently F10 also works. M-` is a bit cumbersome on a Swedish keyboard (ESC, SHIFT-', SPACE).

---

### Post by mali2297 on 2007-11-06
> **keenlearner said:**
> 
Specifically, the first problem when I press M-f it access the menu of terminal. 


Look in the preferences for the terminal. (Is it the default Gnome-terminal?)
You should be able to change the keyboard shortcuts.

---

### Post by keenlearner on 2007-11-06
Thanks, yeah, I never checkout those menu until today. Thanks all is working like what I want. Except I can't access those emacs menu in terminal.

---

