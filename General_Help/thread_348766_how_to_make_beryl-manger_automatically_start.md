---
title: "how to make beryl-manger automatically start?"
date: 2007-01-29
forum: General Help
---

### Post by wwuster on 2007-01-29
I installed beryl using synaptic and it runs perfectly if I run 'beryl-manager' from the command line. How can I make it start automatically when I reboot? I'm running edgy / gnome.

thanks,
William

---

### Post by Ramses de Norre on 2007-01-29
System>Preferences>Sessions>Startup Programs and add it there.

---

### Post by glabouni on 2007-01-29
beware that if for some reasons beryl-manager crashes your x session, you'll end up in xterm.
see:
[http://ubuntuforums.org/showthread.php?t=348761](http://ubuntuforums.org/showthread.php?t=348761)

---

### Post by Ramses de Norre on 2007-01-29
That's true.. And I'd never do it myself but some people like to do so anyway..

---

### Post by glabouni on 2007-01-29
actually I did it myself, without any noticeable problems on my own computer (nvidia). 

But I also did it on 3 others computers, the first with no problems whatsoever (ATI), the other two with difficulties (xorg not starting). 
the first (nvidia) fixed in a matter of minutes with the help of a recent xorg.conf backup and some uninstall/reinstall of packages, the second one (ATI) went through a full reinstallation after 45 minutes spent trying to fix it. 

all 4 of these computers were running beryl perfectly till an update broke them

so I guess it's worth warning people that automatically starting beryl-manager can be a problem in case a beryl update would break your xserver.
my advice would be to remove auto-start of beryl before updating it.

---

### Post by Ramses de Norre on 2007-01-29
Yes you're absolutely right. And I think the fastest way to stop beryl from starting is aliasing beryl-manager to ```
beryl-manager --no-force-window-manager --no-force-decorator
``` which would make that although beryl-manager is started it wont load his window manager nor emerald.

(In fact this helped me out an hour ago when I imported a way too large image into the reflection plug-in and couldn't start beryl-manager without crashing)

---

### Post by glabouni on 2007-01-29
*bonk*
now that you've written it and I've read it: it's so obvious.
I wish I'd have read this thread a couple weeks ago, would have saved me quite some time.

---

### Post by Ramses de Norre on 2007-01-29
Man pages :)

---

### Post by glabouni on 2007-01-29
actually it's the aliasing part that eluded me for some reason ^^

---

### Post by stickx911 on 2007-06-13
I am having a similar problem. I recently did a stream of updates and beryl does not start up on its own. It's in the startup programs, but I guess it crashes while trying to load? When everything else is up I can open it and it works fine...it just doesn't want to start-up with the OS.

is there a simple fix I'm missing?

---

