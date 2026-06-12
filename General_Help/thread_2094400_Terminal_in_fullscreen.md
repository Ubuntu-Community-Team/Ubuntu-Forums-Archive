---
title: "Terminal in fullscreen"
date: 2012-12-13
forum: General Help
---

### Post by dajofeno on 2012-12-13
Hi there!

I'm looking for a command that sets my terminal in fullscreen, and then another that gets out of full screen. I only found the "gnome-terminal --full-screen" but this opens a new terminal, and I want to resize the one I'm in right now.

Regards

---

### Post by CharlesA on 2012-12-13
alt + enter ?

I have never needed to use a terminal "full screen." The closest I get is maximizing the window, or hitting ctrl + alt + f1, etc.

---

### Post by dajofeno on 2012-12-13
I'm not looking for a shortcut, I'm looking for a command that I can run in the terminal..

---

### Post by lykwydchykyn on 2012-12-13
This isn't a native terminal command, but you can install wmctrl and do something like this:
```

wmctrl -r :ACTIVE: -b add,fullscreen

```

Actually, this would be better:
```

wmctrl -r :ACTIVE: -b toggle,fullscreen

```

Note that putting this in a script may have unintended consequences, since ":ACTIVE:" refers to the currently active window.  If you're typing this into a terminal, then naturally it will be active.

---

### Post by jerome1232 on 2012-12-13
> **dajofeno said:**
> I'm not looking for a shortcut, I'm looking for a command that I can run in the terminal..

AFAIK the window manager handles these things, so (assuming you are using unity) I'd look at a compiz command if one exists to full-screen a specific window.

if neither gnome-terminal nor compiz have a command line option for doing so then your next best is the wmctrl approach detailed above.

Why is it you can't rely on the keyboard shortcut of F11 and you need a command?

---

### Post by Cheesemill on 2012-12-13
+1 for F11.

Or you could always switch to a TTY instead using CTRL+ALT+F1.

---

