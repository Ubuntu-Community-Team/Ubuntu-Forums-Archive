---
title: "Fork applications to the background?"
date: 2008-03-27
forum: General Help
---

### Post by xvedejas on 2008-03-27
I've seen this done with terminals in screenshots before; how would I do this?

---

### Post by diegosouza on 2008-03-27
I think you're looking for the CTRL+Z while a exec is running   :-)

jobs: print list of jobs
CTRL+Z: suspend current process
command &: run command in background
bg n: resume background job n
fg n: resume foreground job n

---

### Post by arbulus on 2008-03-27
> **diegosouza said:**
> I think you're looking for the CTRL+Z while a exec is running   :-)

jobs: print list of jobs
CTRL+Z: suspend current process
command &: run command in background
bg n: resume background job n
fg n: resume foreground job n


I was thinking that OP was looking for the way to embed the terminal into the desktop wallpaper.

That I'm not sure how to do.

---

### Post by Oldsoldier2003 on 2008-03-27
> **xvedejas said:**
> I've seen this done with terminals in screenshots before; how would I do this?

are you trying to actually fork a process or are you trying to make it to where the program doesn't close if you close the terminal.

to start a process in the background append & to the command
to prevent a process from closing if you close the shell prepend the command with nohup.

nohup tells the program to notlisten for hangup signals.

---

### Post by p_quarles on 2008-03-27
> **arbulus said:**
> I was thinking that OP was looking for the way to embed the terminal into the desktop wallpaper.

That I'm not sure how to do.
I don't think it's possible to embed an application within an image. What you are referring to, I believe, is a maximized, transparent terminal emulator without any window decorations. Removing window decorations can be done with emulators such as xterm or urxvt. It can also be done with window managers such as Fluxbox or Openbox.

---

### Post by arbulus on 2008-03-27
I just ran across these howtos, a couple of different ways of going about it.  If I was correct about what you are looking for, this should do it for you.

Using Compiz Fusion
[http://ubuntology.com/2007/10/25/howto-embedded-terminal-on-your-gutsy-desktop/](http://ubuntology.com/2007/10/25/howto-embedded-terminal-on-your-gutsy-desktop/)

Using Devispie
[http://ubuntuforums.org/showthread.php?t=202249&highlight=terminal+desktop](http://ubuntuforums.org/showthread.php?t=202249&highlight=terminal+desktop)

Hope this helps!

---

### Post by xvedejas on 2008-03-27
Thanks; that is exactly what I was looking for!

---

