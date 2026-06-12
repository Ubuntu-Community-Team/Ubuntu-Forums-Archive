---
title: "subtle differences in window manager and decorator"
date: 2008-06-23
forum: General Help
---

### Post by sea_monkey987 on 2008-06-23
I'm having trouble understanding exactly whether certain packages are window manager or decorators.

    1) In ubuntu-desktop, when one goes to the appearance and selects a theme, he is customizing the window decorator, right?
    2) If installing from scratch, can one skip the window decorator all together and still have window borders with just the window manager.
    3) Is xfwm4 a window manager or decorator.  I ask this because the tutorial here [http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/](http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/) to put compiz on xubuntu calls it both.  He compares xfwm4 to emerald which I know to be a window decorator.
    4) With all the desktop effects turned off, what is the default window decorator in ubuntu-desktop?
    5) I've read that compiz-fusion is a compositing window manager; therefore, it needs another window manager in order to be able to draw windows.  However, in the system monitor, metacity isn't running when compiz is and vice-versa.

I've tried searching around but I've read conflicting things.  Clearly, I'm confused.  I would appreciate it if someone could clear up the terminology for me.

---

### Post by sdennie on 2008-06-23
1) You are either setting the gtk theme or the window manager theme.  More below.

2) It depends.  Compiz is odd in that it's a "window manager" but, still needs something to decorate the windows (gtk-window-decorator or emerald).  If you aren't using compiz it's much more straightforward: The window manager decorates the windows.

3) xfwm4 is a traditional window manager

4) metacity

5) See #2.

Hope that helps.

---

### Post by sea_monkey987 on 2008-06-23
That certainly does.  Thanks.  So, metacity is both a window manager and window decorator?

---

### Post by sdennie on 2008-06-23
As far as I know, the idea of a "window decorator" is sort of an invention of compiz.  For about 25 years, in X, the "window manager" was the thing that drew the borders around the windows.  Because compiz is a fairly radical shift in the way things are done, they made decorations pluggable and not part of the default behavior of the window manager.

---

### Post by sea_monkey987 on 2008-06-23
Thanks.  That clears things up a lot.  I was making a live cd by installing packages with just the core ubuntu installed.  In an effort to seriosly shrink a usuable live cd, I tried skipping the ubuntu-desktop package and installing gnome-core, compiz, gdm, etc.  It worked; however, it looked awful!  I tried the human theme shipped with ubuntu and it seemed to be only installed partially.  Is the gtk-window-decorator something I needed to install?

---

### Post by sdennie on 2008-06-23
Probably.  The output of dpkg -S is this:

```

$ dpkg -S /usr/bin/gtk-window-decorator 
compiz-gnome: /usr/bin/gtk-window-decorator

```

So, you'd need the compiz-gnome package.

---

### Post by sea_monkey987 on 2008-06-28
sorry for the delay. I had to close the window and then couldn't find this thread again.  I will try your idea and get back with the results.  I have to start from scratch, though.

---

