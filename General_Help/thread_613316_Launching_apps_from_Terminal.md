---
title: "Launching apps from Terminal"
date: 2007-11-14
forum: General Help
---

### Post by JShadow007 on 2007-11-14
Hello,

I'm a completely new Ubuntu user, with not much linux experience.  I'm running ubuntu on an older laptop whose trackpad isn't wonderful, so launch applications from menus can be a bit cumbersome, and i just launch them from terminal.


Anytime I accidentally close the terminal window, however, all of the programs close too.  I was told that opening a program like so:

firefox&

would keep programs open even if the terminal window closed.  But it doesn't seem to work for me.  What can I do to be able to launch from terminal and be able to close the terminal window without ending the programs?

I'm running 7.04, and I update regularly.


Thanks!

---

### Post by shad0w_walker on 2007-11-14
I'm not sure what to suggest about keeping them open when you close the terminal, but have you considering using the keyboard to navigate the applications menu? Pressing Alt + F1 should open the Applications menu and you can navigate from there using the arrow keys.

---

### Post by JShadow007 on 2007-11-15
I updated to 7.10, but I'm still running into the problem.

Thanks for the workaround shad0w--it's certianly better than nothing, and a bit easier than working with this touchpad.

---

### Post by kpkeerthi on 2007-11-15
Or press ALT + F2 and enter your program name there.

---

### Post by jayjaygibbs on 2008-02-05
There is a way to close the terminal and keep the apps running. 

Does anyone know how seeing as that's what I'm looking for??

---

### Post by seventhc on 2008-02-05
Well I just tested this with firefox
1: if I do **firefox &** and shut the terminal then firefox closes, if I enter the full path, like so:
```
/usr/bin/firefox &
```then I can close the terminal and firefox stays open.
If you need to find the path for a program you can open a terminal and type:
```
which programname
```in my example I would have put *which firefox*.
hope this helps, I do beleive it might be easier to just use the suggestion above <alt-F2>tthen you would just enter firefox, the box would close and firefox would launch. :)

---

### Post by jayjaygibbs on 2008-02-05
> **seventhc said:**
>  I do beleive it might be easier to just use the suggestion above <alt-F2>tthen you would just enter firefox, the box would close and firefox would launch. :)

I use IceWm so I've not got that option. There is a way which is slightly easier then the way you showed though. I can't remember what it is though.

it was something like thunar -b or something if opening thunar

---

### Post by seventhc on 2008-02-05
Oh, I'm not to familiar with IceWm, never used it. :( I don't think you mentioned that earlier either. ;)
So the other option doesn't work either then?? (I mean using the full path)

---

### Post by pjkoczan on 2008-02-05
Are you using GNOME, by any chance (the ubuntu default)?

I've seen this happen in GNOME but I didn't see it when running fvwm2 (an old-as-dirt lightweight window manager), no matter what terminal I was using (xterm, gnome-terminal, etc). There's probably something in GNOME that strictly enforces when a shell (the parent process) dies, it takes every child process with it instead of re-parenting them.

The question is, is this something in the default config that can be easily overridden, or is this something in GNOME that you'll just have to live with (or use another window manager)? I couldn't find anything in the online help to find an answer. Hopefully this can push you in the right direction.

---

### Post by Dark Master Schmidt on 2008-02-05
```
firefox & exit
```

---

