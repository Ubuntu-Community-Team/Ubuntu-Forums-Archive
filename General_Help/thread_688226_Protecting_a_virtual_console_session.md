---
title: "Protecting a virtual console session"
date: 2008-02-05
forum: General Help
---

### Post by imbjr on 2008-02-05
I am cursed with an ATI card, which means that every so often, when I leave myself logged in to do some lengthy rendering job and the wife comes along, logs in, does her surfing and then logs out - the system has a fit and a reboot is required.

Fortunately, the render can be continued from where it got to, but even better I realised that I can leave the render going in a virtual console session and log out of the graphical frontend, allowing the wife access without risk of taking down the system.

However, that virtual console session has no protection on it. A quick ctrl+alt+F1 will reveal it and leave it open to being cancelled - though this is actually not very likely. Still, the principle is sound: how do I protect such a session ...

... or is there another way of running applications without X but having the full protection of a password?

---

### Post by jrib on 2008-02-05
Use screen.  (You don't need the virtual console, but you can use it there too if you want).

Quick intro:
1. Type 'screen' in a shell.
2. run your render
3. detach screen (ctrl-a d)
4. logout, let wife use computer
5. log in (does not matter if you use a virtual console or go back to X, you just need a shell)
6. reattach the screen session (screen -r)

Also see:
[http://www.kuro5hin.org/story/2004/3/9/16838/14935](http://www.kuro5hin.org/story/2004/3/9/16838/14935)
[http://en.wikipedia.org/wiki/GNU_Screen](http://en.wikipedia.org/wiki/GNU_Screen)

By the way, if you decide to use screen in the virtual console and do not want to detach and logout, you can lock screen with ctrl-a x

---

### Post by imbjr on 2008-02-05
Yup, looks like that's that ticket.

Man, I love this OS.

---

